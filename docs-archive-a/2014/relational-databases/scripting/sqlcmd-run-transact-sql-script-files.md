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
# <a name="run-transact-sql-script-files-using-sqlcmd"></a><span data-ttu-id="1055a-102">sqlcmd を使用した Transact-SQL スクリプト ファイルの実行</span><span class="sxs-lookup"><span data-stu-id="1055a-102">Run Transact-SQL Script Files Using sqlcmd</span></span>
  <span data-ttu-id="1055a-103">`sqlcmd` を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを実行できます。</span><span class="sxs-lookup"><span data-stu-id="1055a-103">You can use `sqlcmd` to run a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file.</span></span> <span data-ttu-id="1055a-104">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント、`sqlcmd` コマンド、およびスクリプト変数を組み合わせて記述できるテキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="1055a-104">A [!INCLUDE[tsql](../../includes/tsql-md.md)] script file is a text file that can contain a combination of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, `sqlcmd` commands, and scripting variables.</span></span>  
  
 <span data-ttu-id="1055a-105">メモ帳を使用して簡単な [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="1055a-105">To create a simple [!INCLUDE[tsql](../../includes/tsql-md.md)] script file by using Notepad, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1055a-106">**[スタート]** ボタンをクリックし、 **[すべてのプログラム]**、 **[アクセサリ]** の順にポイントして、 **[メモ帳]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1055a-106">Click **Start**, point to **All Programs**, point to **Accessories**, and then click **Notepad**.</span></span>  
  
2.  <span data-ttu-id="1055a-107">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードをコピーして、メモ帳に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1055a-107">Copy and paste the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code into Notepad:</span></span>  
  
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
  
3.  <span data-ttu-id="1055a-108">作成したファイルを **myScript.sql** という名前で C ドライブに保存します。</span><span class="sxs-lookup"><span data-stu-id="1055a-108">Save the file as **myScript.sql** in the C drive.</span></span>  
  
### <a name="to-run-the-script-file"></a><span data-ttu-id="1055a-109">スクリプト ファイルを実行するには</span><span class="sxs-lookup"><span data-stu-id="1055a-109">To run the script file</span></span>  
  
1.  <span data-ttu-id="1055a-110">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1055a-110">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="1055a-111">コマンド プロンプト ウィンドウで、「`sqlcmd -S myServer\instanceName -i C:\myScript.sql`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1055a-111">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql`</span></span>  
  
3.  <span data-ttu-id="1055a-112">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1055a-112">Press ENTER.</span></span>  
  
 <span data-ttu-id="1055a-113">[!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] の従業員名と住所の一覧がコマンド プロンプト ウィンドウに出力されます。</span><span class="sxs-lookup"><span data-stu-id="1055a-113">A list of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] employee names and addresses is written to the command prompt window.</span></span>  
  
### <a name="to-save-this-output-to-a-text-file"></a><span data-ttu-id="1055a-114">出力をテキスト ファイルに保存するには</span><span class="sxs-lookup"><span data-stu-id="1055a-114">To save this output to a text file</span></span>  
  
1.  <span data-ttu-id="1055a-115">コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1055a-115">Open a command prompt window.</span></span>  
  
2.  <span data-ttu-id="1055a-116">コマンド プロンプト ウィンドウで、「`sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1055a-116">In the Command Prompt window, type: `sqlcmd -S myServer\instanceName -i C:\myScript.sql -o C:\EmpAdds.txt`</span></span>  
  
3.  <span data-ttu-id="1055a-117">Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1055a-117">Press ENTER.</span></span>  
  
 <span data-ttu-id="1055a-118">コマンド プロンプト ウィンドウには何も出力されません。</span><span class="sxs-lookup"><span data-stu-id="1055a-118">No output is returned in the Command Prompt window.</span></span> <span data-ttu-id="1055a-119">代わりに、EmpAdds.txt ファイルに出力されます。</span><span class="sxs-lookup"><span data-stu-id="1055a-119">Instead, the output is sent to the EmpAdds.txt file.</span></span> <span data-ttu-id="1055a-120">EmpAdds.txt を開くと、この出力を確認できます。</span><span class="sxs-lookup"><span data-stu-id="1055a-120">You can verify this output by opening the EmpAdds.txt file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1055a-121">参照</span><span class="sxs-lookup"><span data-stu-id="1055a-121">See Also</span></span>  
 <span data-ttu-id="1055a-122">[sqlcmd ユーティリティの起動](sqlcmd-start-the-utility.md) </span><span class="sxs-lookup"><span data-stu-id="1055a-122">[Start the sqlcmd Utility](sqlcmd-start-the-utility.md) </span></span>  
 [<span data-ttu-id="1055a-123">sqlcmd Utility</span><span class="sxs-lookup"><span data-stu-id="1055a-123">sqlcmd Utility</span></span>](../../tools/sqlcmd-utility.md)  
  
  
