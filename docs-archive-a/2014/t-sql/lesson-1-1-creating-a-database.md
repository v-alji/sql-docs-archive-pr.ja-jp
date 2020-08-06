---
title: データベースの作成 (チュートリアル) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- tutorial creating a database
ms.assetid: e1e2c83f-dfad-4bb8-aa7a-09d3f69517ae
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 99d5439c289b5d4e71786d4c6734f158f6bba371
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642445"
---
# <a name="creating-a-database-tutorial"></a><span data-ttu-id="e9da1-102">データベースの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="e9da1-102">Creating a Database (Tutorial)</span></span>
  <span data-ttu-id="e9da1-103">多くの [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント同様、CREATE DATABASE ステートメントには、必須パラメーターがあります。必須パラメーターはデータベースの名前です。</span><span class="sxs-lookup"><span data-stu-id="e9da1-103">Like many [!INCLUDE[tsql](../includes/tsql-md.md)] statements, the CREATE DATABASE statement has a required parameter: the name of the database.</span></span> <span data-ttu-id="e9da1-104">また、CREATE DATABASE には、データベース ファイルを配置するディスクの場所など、多くのオプションのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="e9da1-104">CREATE DATABASE also has many optional parameters, such as the disk location where you want to put the database files.</span></span> <span data-ttu-id="e9da1-105">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] でオプション パラメーターを指定せずに CREATE DATABASE を実行すると、これらの多くのパラメーターでは既定の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9da1-105">When you execute CREATE DATABASE without the optional parameters, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] uses default values for many of these parameters.</span></span> <span data-ttu-id="e9da1-106">このチュートリアルでは、オプションの構文パラメーターをほとんど使用しません。</span><span class="sxs-lookup"><span data-stu-id="e9da1-106">This tutorial uses very few of the optional syntax parameters.</span></span>  
  
### <a name="to-create-a-database"></a><span data-ttu-id="e9da1-107">データベースを作成するには</span><span class="sxs-lookup"><span data-stu-id="e9da1-107">To create a database</span></span>  
  
1.  <span data-ttu-id="e9da1-108">クエリ エディターのウィンドウで、次のコードを入力します。ただし実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="e9da1-108">In a Query Editor window, type but do not execute the following code:</span></span>  
  
    ```  
    CREATE DATABASE TestData  
    GO  
    ```  
  
2.  <span data-ttu-id="e9da1-109">ポインターを使用して `CREATE DATABASE`の語句を選択し、 **F1**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e9da1-109">Use the pointer to select the words `CREATE DATABASE`, and then press **F1**.</span></span> <span data-ttu-id="e9da1-110">SQL Server オンライン ブックの CREATE DATABASE のトピックが開きます。</span><span class="sxs-lookup"><span data-stu-id="e9da1-110">The CREATE DATABASE topic in SQL Server Books Online should open.</span></span> <span data-ttu-id="e9da1-111">この方法を使用して、このチュートリアルで使用する CREATE DATABASE やその他のステートメントの全構文を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="e9da1-111">You can use this technique to find the complete syntax for CREATE DATABASE and for the other statements that are used in this tutorial.</span></span>  
  
3.  <span data-ttu-id="e9da1-112">クエリ エディターで、 **F5** キーを押してステートメントを実行し、 `TestData`という名前のデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9da1-112">In Query Editor, press **F5** to execute the statement and create a database named `TestData`.</span></span>  
  
 <span data-ttu-id="e9da1-113">データベースを作成すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって **モデル** データベースのコピーが作成され、その名前がデータベース名に変更されます。</span><span class="sxs-lookup"><span data-stu-id="e9da1-113">When you create a database, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] makes a copy of the **model** database, and renames the copy to the database name.</span></span> <span data-ttu-id="e9da1-114">オプション パラメーターでデータベースに大きな初期サイズを指定しなければ、この操作は数秒で完了します。</span><span class="sxs-lookup"><span data-stu-id="e9da1-114">This operation should only take several seconds, unless you specify a large initial size of the database as an optional parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e9da1-115">GO キーワードは、複数のステートメントを単一のバッチで送信した場合に、ステートメントを区切ります。</span><span class="sxs-lookup"><span data-stu-id="e9da1-115">The keyword GO separates statements when more than one statement is submitted in a single batch.</span></span> <span data-ttu-id="e9da1-116">GO は、バッチにステートメントが 1 つしか入っていない場合はオプションです。</span><span class="sxs-lookup"><span data-stu-id="e9da1-116">GO is optional when the batch contains only one statement.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="e9da1-117">このレッスンの次の作業</span><span class="sxs-lookup"><span data-stu-id="e9da1-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="e9da1-118">テーブルの作成 (チュートリアル)</span><span class="sxs-lookup"><span data-stu-id="e9da1-118">Creating a Table &#40;Tutorial&#41;</span></span>](lesson-1-2-creating-a-table.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9da1-119">参照</span><span class="sxs-lookup"><span data-stu-id="e9da1-119">See Also</span></span>  
 [<span data-ttu-id="e9da1-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e9da1-120">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
