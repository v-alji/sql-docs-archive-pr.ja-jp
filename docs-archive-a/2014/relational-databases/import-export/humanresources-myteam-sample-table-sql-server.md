---
title: HumanResources.myTeam サンプル テーブル (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643345"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a><span data-ttu-id="0fca2-102">HumanResources.myTeam サンプル テーブル (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0fca2-102">HumanResources.myTeam Sample Table (SQL Server)</span></span>
  <span data-ttu-id="0fca2-103">「 [一括データのインポートおよびエクスポート](bulk-import-and-export-of-data-sql-server.md) 」のコード例の大部分では、 **myTeam**という名前の特殊なテスト用テーブルが必要になります。</span><span class="sxs-lookup"><span data-stu-id="0fca2-103">Many of the code examples in [Importing and Exporting Bulk Data](bulk-import-and-export-of-data-sql-server.md) require a special-purpose test table named **myTeam**.</span></span> <span data-ttu-id="0fca2-104">これらのコード例を実行する前に、 **データベースの** HumanResources **スキーマに** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] テーブルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0fca2-104">Before you can run the examples, you must create the **myTeam** table in the **HumanResources** schema of the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] <span data-ttu-id="0fca2-105">は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のサンプル データベースの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="0fca2-105">is one of the sample databases in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="0fca2-106">**myTeam** には、次の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0fca2-106">The **myTeam** table is contains the following columns.</span></span>  
  
|<span data-ttu-id="0fca2-107">列</span><span class="sxs-lookup"><span data-stu-id="0fca2-107">Column</span></span>|<span data-ttu-id="0fca2-108">データ型</span><span class="sxs-lookup"><span data-stu-id="0fca2-108">Data type</span></span>|<span data-ttu-id="0fca2-109">NULL 値の許容</span><span class="sxs-lookup"><span data-stu-id="0fca2-109">Nullability</span></span>|<span data-ttu-id="0fca2-110">説明</span><span class="sxs-lookup"><span data-stu-id="0fca2-110">Description</span></span>|  
|------------|---------------|-----------------|-----------------|  
|<span data-ttu-id="0fca2-111">**EmployeeID**</span><span class="sxs-lookup"><span data-stu-id="0fca2-111">**EmployeeID**</span></span>|`smallint`|<span data-ttu-id="0fca2-112">不可</span><span class="sxs-lookup"><span data-stu-id="0fca2-112">Not null</span></span>|<span data-ttu-id="0fca2-113">行の主キー。</span><span class="sxs-lookup"><span data-stu-id="0fca2-113">Primary key for the rows.</span></span> <span data-ttu-id="0fca2-114">チーム メンバーの従業員 ID。</span><span class="sxs-lookup"><span data-stu-id="0fca2-114">Employee ID of a member of my team.</span></span>|  
|<span data-ttu-id="0fca2-115">**名前**</span><span class="sxs-lookup"><span data-stu-id="0fca2-115">**Name**</span></span>|`nvarchar(50)`|<span data-ttu-id="0fca2-116">不可</span><span class="sxs-lookup"><span data-stu-id="0fca2-116">Not null</span></span>|<span data-ttu-id="0fca2-117">チーム メンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="0fca2-117">Name of a member of my team.</span></span>|  
|<span data-ttu-id="0fca2-118">**Title**</span><span class="sxs-lookup"><span data-stu-id="0fca2-118">**Title**</span></span>|`nvarchar(50)`|<span data-ttu-id="0fca2-119">Nullable</span><span class="sxs-lookup"><span data-stu-id="0fca2-119">Nullable</span></span>|<span data-ttu-id="0fca2-120">チームにおける従業員の肩書き。</span><span class="sxs-lookup"><span data-stu-id="0fca2-120">Title the employee performs on my team.</span></span>|  
|<span data-ttu-id="0fca2-121">**バックグラウンド**</span><span class="sxs-lookup"><span data-stu-id="0fca2-121">**Background**</span></span>|`nvarchar(50)`|<span data-ttu-id="0fca2-122">不可</span><span class="sxs-lookup"><span data-stu-id="0fca2-122">Not null</span></span>|<span data-ttu-id="0fca2-123">行が最後に更新された日時</span><span class="sxs-lookup"><span data-stu-id="0fca2-123">Date and time the row was last updated.</span></span> <span data-ttu-id="0fca2-124">(既定値)。</span><span class="sxs-lookup"><span data-stu-id="0fca2-124">(Default)</span></span>|  
  
 <span data-ttu-id="0fca2-125">**HumanResources.myTeam テーブルを作成するには**</span><span class="sxs-lookup"><span data-stu-id="0fca2-125">**To create HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="0fca2-126">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0fca2-126">Use the following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements:</span></span>  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 <span data-ttu-id="0fca2-127">**HumanResources.myTeam テーブルに行を設定するには**</span><span class="sxs-lookup"><span data-stu-id="0fca2-127">**To populate HumanResources.myTeam**</span></span>  
  
-   <span data-ttu-id="0fca2-128">次の `INSERT` ステートメントでは、テーブルに 2 つの行を設定します。</span><span class="sxs-lookup"><span data-stu-id="0fca2-128">Execute following `INSERT` statements to populate the table with two rows:</span></span>  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="0fca2-129">これらのステートメントでは、4 番目の列 `Background`がスキップされます。</span><span class="sxs-lookup"><span data-stu-id="0fca2-129">These statements skip the fourth column, `Background`.</span></span> <span data-ttu-id="0fca2-130">この行には既定値が設定されています。</span><span class="sxs-lookup"><span data-stu-id="0fca2-130">This has a default value.</span></span> <span data-ttu-id="0fca2-131">この列をスキップすると、この `INSERT` ステートメントを実行した際に、この列が空欄のままになります。</span><span class="sxs-lookup"><span data-stu-id="0fca2-131">Skipping this column causes this `INSERT` statement to leave this column blank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fca2-132">参照</span><span class="sxs-lookup"><span data-stu-id="0fca2-132">See Also</span></span>  
 [<span data-ttu-id="0fca2-133">データの一括インポートと一括エクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0fca2-133">Bulk Import and Export of Data &#40;SQL Server&#41;</span></span>](bulk-import-and-export-of-data-sql-server.md)  
  
  
