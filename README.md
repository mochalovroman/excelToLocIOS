excelToLocIOS
=============

create loc file for xcode projects of excel with localization

Надо создать из приведенного ниже кода .py файл, изменить имя excel файла и скомпилить его в директории с этим файлом

```
import xlrd
rb = xlrd.open_workbook('LocalizeProject.xlsx', formatting_info=False)
sh = rb.sheet_by_index(0)
sheet = rb.sheet_by_index(0)
for rownum in range(sheet.nrows): 
	logfile = open("En.strings", "a")

	columnAx = sh.cell_value(rowx=rownum, colx=0)
	if isinstance(columnAx, float):itogColumn0 = str(int(columnAx) ) 
	else:itogColumn0 = columnAx.encode('utf-8')
  
	columnBxEN = sh.cell_value(rowx=rownum, colx=1)
  	if isinstance(columnBxEN, float):itogColumn1En = str(int(columnBxEN) ) 
	else:itogColumn1En = columnBxEN.encode('utf-8')

	fullString=('"'+itogColumn0+'"').ljust(40)+" ="+'"'+itogColumn1En+'";'
	if itogColumn0[0:2]=='//':fullString=itogColumn0 
	if itogColumn0[0:2]=='':fullString=itogColumn0
	logfile.write(fullString+"\n")
	logfile.close()
print "SUCCESS EN LOC FILE"

for rownum in range(sheet.nrows): 
	logfile = open("Ru.strings", "a")

	columnAx = sh.cell_value(rowx=rownum, colx=0)
	if isinstance(columnAx, float):itogColumn0 = str(int(columnAx) ) 
	else:itogColumn0 = columnAx.encode('utf-8')
  
	columnCxRU = sh.cell_value(rowx=rownum, colx=2)
  	if isinstance(columnCxRU, float):itogColumn2Ru = str(int(columnCxRU) ) 
	else:itogColumn2Ru = columnCxRU.encode('utf-8')

	fullString=('"'+itogColumn0+'"').ljust(40)+" ="+'"'+itogColumn2Ru+'";'
	if itogColumn0[0:2]=='//':fullString=itogColumn0 
	if itogColumn0[0:2]=='':fullString=itogColumn0
	logfile.write(fullString+"\n")
	logfile.close()
print "SUCCESS RU LOC FILE"

```
