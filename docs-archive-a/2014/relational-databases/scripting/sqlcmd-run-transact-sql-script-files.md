---
title: sqlcmd を使用した Transact-SQL スクリプト ファイルの実行
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- transact sql scripts
ms.assetid: 90067eb8-ca3e-44e8-bb1a-bf7d1a359423
author: rothja
ms.author: jroth
ms.openlocfilehash: cd34b089fc4e971cac9e5713cbe303192a7a48c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633044"
---
# <a name="run-transact-sql-script-files-using-sqlcmd"></a>sqlcmd を使用した Transact-SQL スクリプト ファイルの実行
  `sqlcmd` を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを実行できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、`sqlcmd` コマンド、およびスクリプト変数を組み合わせて記述できるテキスト ファイルです。  
  
 メモ帳を使用して簡単な [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[アクセサリ]** の順にポイントして、 **[メモ帳]** をクリックします。  
  
2.  次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードをコピーして、メモ帳に貼り付けます。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SELECT p.FirstName + ' ' + p.LastName AS 'Employee Name',  
    a.AddressLine1, a.AddressLine2 , a.City, a.PostalCode   
    FROM Person.Person AS p   
       INNER JOIN HumanResources.Employee AS e   
            ON p.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.BusinessEntityAddress bea   
            ON bea.BusinessEntityID = e.BusinessEntityID  
        INNER JOIN Person.Address AS a   
            ON a.AddressID = bea.AddressID;  
    GO  
    ```  
  
3.  作成したファイルを **myScript.sql** という名前で C ドライブに保存します。  
  
### <a name="to-run-the-script-file"></a>スクリプト ファイルを実行するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  コマンド プロンプト ウィンドウで、「`sqlcmd -S myServer\instanceName -i C:\myScript.sql`」と入力します。  
  
3.  Enter キーを押します。  
  
 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] の従業員名と住所の一覧がコマンド プロンプト ウィンドウに出力されます。  
  
### <a name="to-save-this-output-to-a-text-file"></a>出力をテキスト ファイルに保存するには  
  
1.  コマンド プロンプト ウィンドウを開きます。  
  
2.  コマンド プロンプト ウィンドウで、「`sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`」と入力します。  
  
3.  Enter キーを押します。  
  
 コマンド プロンプト ウィンドウには何も出力されません。 代わりに、EmpAdds.txt ファイルに出力されます。 EmpAdds.txt を開くと、この出力を確認できます。  
  
## <a name="see-also"></a>参照  
 [sqlcmd ユーティリティの起動](sqlcmd-start-the-utility.md)   
 [sqlcmd Utility](../../tools/sqlcmd-utility.md)  
  
  
