```apex
Blob data = new ExcelGenerator().GetZipFile(
'header1', 'header2', 'header3', 'header4', 'header5', 'header6', 'header7', 'header8',
'value1', 'value2', 'value3', 'value4', 'value5', 'value6', 'value7', 'value8');
Account testAcc = [SELECT Id FROM Account WHERE Name LIKE 'Test%' LIMIT 1];
Attachment attachment = new Attachment();
attachment.Body = data;
attachment.Name = String.valueOf('Sample.xlsx');
attachment.ParentId = testAcc.Id;
Database.SaveResult result = Database.insert(attachment, true);
System.debug(result);
System.debug('/servlet/servlet.FileDownload?file=' + result.getId());
```
