# Power-Query-Completing-the-time-period

![grafik](https://user-images.githubusercontent.com/84840321/161085884-728767ca-6185-49d8-923c-cbf181d249bd.png)

let

    Source = Excel.CurrentWorkbook(){[Name="Table1"]}[Content],
    
    ListZip = {"class"}&List.Transform(List.Zip({{8..12},{9..13}}),(x)=>Text.From(x{0})&" - Uhr"),
    
    TableToRows = Table.FromRows({},ListZip) &Source,
    
    #"Replaced Value" = Table.ReplaceValue(TableToRows,null,0,Replacer.ReplaceValue,Table.ColumnNames(TableToRows))
    
in

    #"Replaced Value"
    
    
![grafik](https://user-images.githubusercontent.com/84840321/161085971-78f14c5e-2c3c-483b-8f17-2cc66b7285cc.png)
