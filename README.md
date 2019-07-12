# How-To-Import-Excel-in-Java-JTable-GUI-Swing-Application-Tutorial-Netbeans
How To Import Excel in Java JTable GUI Swing Application Tutorial Netbeans
For More Details - http://mauricemuteti.info/how-to-import-excel-in-java-jtable-gui-swing-application-tutorial-netbeans/

<pre>
[code lang="java"]

public void importExcelToJtableJava() {

        File excelFile;
        FileInputStream excelFIS = null;
        BufferedInputStream excelBIS = null;
        XSSFWorkbook excelImportToJTable = null;
        String defaultCurrentDirectoryPath = "C:\\Users\\Authentic\\Desktop";
        JFileChooser excelFileChooser = new JFileChooser(defaultCurrentDirectoryPath);
        excelFileChooser.setDialogTitle("Select Excel File");
        FileNameExtensionFilter fnef = new FileNameExtensionFilter("EXCEL FILES", "xls", "xlsx", "xlsm");
        excelFileChooser.setFileFilter(fnef);
        int excelChooser = excelFileChooser.showOpenDialog(null);
        if (excelChooser == JFileChooser.APPROVE_OPTION) {
            try {
                excelFile = excelFileChooser.getSelectedFile();
                excelFIS = new FileInputStream(excelFile);
                excelBIS = new BufferedInputStream(excelFIS);
                excelImportToJTable = new XSSFWorkbook(excelBIS);
                XSSFSheet excelSheet = excelImportToJTable.getSheetAt(0);

                for (int row = 0; row < excelSheet.getLastRowNum(); row++) {
                    XSSFRow excelRow = excelSheet.getRow(row);

                    XSSFCell excelName = excelRow.getCell(0);
                    XSSFCell excelGender = excelRow.getCell(1);
                    XSSFCell excelProgrammingLanguage = excelRow.getCell(2);
                    XSSFCell excelSubject = excelRow.getCell(3);
                    XSSFCell excelImage = excelRow.getCell(4);

                    JLabel excelJL = new JLabel(new ImageIcon(new ImageIcon(excelImage.getStringCellValue()).getImage().getScaledInstance(60, 60, Image.SCALE_SMOOTH)));
                    model.addRow(new Object[]{excelName, excelGender, excelProgrammingLanguage, excelSubject, excelJL});
                }
                JOptionPane.showMessageDialog(null, "Imported Successfully !!.....");
            } catch (IOException iOException) {
                JOptionPane.showMessageDialog(null, iOException.getMessage());
            } finally {
                try {
                    if (excelFIS != null) {
                        excelFIS.close();
                    }
                    if (excelBIS != null) {
                        excelBIS.close();
                    }
                    if (excelImportToJTable != null) {
                        excelImportToJTable.close();
                    }
                } catch (IOException iOException) {
                    JOptionPane.showMessageDialog(null, iOException.getMessage());
                }
            }
        }
    }  
}
[/code]

</pre>
