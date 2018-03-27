---
title: java开发总结
tags: java
grammar_cjkRuby: true
---

#### poi
POI读取Excel的实际行
try {  
    Workbook hwb = new HSSFWorkbook(  
            new FileInputStream("C:\\1.xls"));  
    Sheet sheet = hwb.getSheetAt(0);  
    //int rowCount = sheet.getPhysicalNumberOfRows();  
  
    int begin = sheet.getFirstRowNum();  
  
    int end = sheet.getLastRowNum();  
  
    for (int i = begin; i <= end; i++) {  
        if (null == sheet.getRow(i)) {  
            continue;  
        }  
        // do something  
    }  
} catch (FileNotFoundException e) {  
    e.printStackTrace();  
} catch (IOException e) {  
    e.printStackTrace();  
}  