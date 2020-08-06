---
title: シノニムの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- sql12.swb.synonym.general.f1
helpviewer_keywords:
- creating synonyms
- synonyms [SQL Server], creating
ms.assetid: fedfa7a5-d0b6-4e2b-90f4-a08122958e33
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3dc18c9d0d6048c4190ba56725dd332f2dfb629e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630860"
---
# <a name="create-synonyms"></a><span data-ttu-id="f4aba-102">シノニムの作成</span><span class="sxs-lookup"><span data-stu-id="f4aba-102">Create Synonyms</span></span>
  <span data-ttu-id="f4aba-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して、シノニムを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-103">This topic describes how to create a synonym in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="f4aba-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="f4aba-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f4aba-105">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="f4aba-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f4aba-106">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f4aba-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f4aba-107">**次を使用してシノニムを作成するには:**</span><span class="sxs-lookup"><span data-stu-id="f4aba-107">**To create a synonym, using:**</span></span>  
  
     [<span data-ttu-id="f4aba-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f4aba-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f4aba-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f4aba-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f4aba-110">はじめに</span><span class="sxs-lookup"><span data-stu-id="f4aba-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f4aba-111">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f4aba-111">Security</span></span>  
 <span data-ttu-id="f4aba-112">ユーザーが特定のスキーマ内にシノニムを作成するには、CREATE SYNONYM 権限が必要であり、さらにスキーマを所有しているか ALTER SCHEMA 権限が与えられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4aba-112">To create a synonym in a given schema, a user must have CREATE SYNONYM permission and either own the schema or have ALTER SCHEMA permission.</span></span> <span data-ttu-id="f4aba-113">CREATE SYNONYM 権限は、譲与可能な権限です。</span><span class="sxs-lookup"><span data-stu-id="f4aba-113">The CREATE SYNONYM permission is a grantable permission.</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f4aba-114">Permissions</span><span class="sxs-lookup"><span data-stu-id="f4aba-114">Permissions</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f4aba-115">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f4aba-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="f4aba-116">シノニムを作成するには</span><span class="sxs-lookup"><span data-stu-id="f4aba-116">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="f4aba-117">**オブジェクト エクスプローラー**で、新しいビューを作成するデータベースを展開します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-117">In **Object Explorer**, expand the database where you want to create your new view.</span></span>  
  
2.  <span data-ttu-id="f4aba-118">**[シノニム]** フォルダーを右クリックし、 **[新しいシノニム...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4aba-118">Right-click the **Synonyms** folder, then click **New Synonym...**.</span></span>  
  
3.  <span data-ttu-id="f4aba-119">**[シノニムの追加]** ダイアログ ボックスで、次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-119">In the **Add Synonym** dialog box, enter the following information.</span></span>  
  
     <span data-ttu-id="f4aba-120">**[シノニム名]**</span><span class="sxs-lookup"><span data-stu-id="f4aba-120">**Synonym name**</span></span>  
     <span data-ttu-id="f4aba-121">このオブジェクトに対して使用する新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-121">Type the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="f4aba-122">**[シノニム スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="f4aba-122">**Synonym schema**</span></span>  
     <span data-ttu-id="f4aba-123">このオブジェクトに対して使用する新しい名前のスキーマを入力します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-123">Type the schema of the new name you will use for this object.</span></span>  
  
     <span data-ttu-id="f4aba-124">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="f4aba-124">**Server name**</span></span>  
     <span data-ttu-id="f4aba-125">接続するサーバー インスタンスを入力します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-125">Type the server instance to connect to.</span></span>  
  
     <span data-ttu-id="f4aba-126">**データベース名**</span><span class="sxs-lookup"><span data-stu-id="f4aba-126">**Database name**</span></span>  
     <span data-ttu-id="f4aba-127">オブジェクトを含んでいるデータベースを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-127">Type or select the database containing the object.</span></span>  
  
     <span data-ttu-id="f4aba-128">**[スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="f4aba-128">**Schema**</span></span>  
     <span data-ttu-id="f4aba-129">オブジェクトを所有しているスキーマを入力または選択します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-129">Type or select the schema that owns the object.</span></span>  
  
     <span data-ttu-id="f4aba-130">**オブジェクトの種類**</span><span class="sxs-lookup"><span data-stu-id="f4aba-130">**Object type**</span></span>  
     <span data-ttu-id="f4aba-131">オブジェクトの型を選択します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-131">Select the type of object.</span></span>  
  
     <span data-ttu-id="f4aba-132">**オブジェクト名です。**</span><span class="sxs-lookup"><span data-stu-id="f4aba-132">**Object name**</span></span>  
     <span data-ttu-id="f4aba-133">シノニムで参照するオブジェクトの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-133">Type the name of the object to which the synonym refers.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f4aba-134">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f4aba-134">Using Transact-SQL</span></span>  
  
#### <a name="to-create-a-synonym"></a><span data-ttu-id="f4aba-135">シノニムを作成するには</span><span class="sxs-lookup"><span data-stu-id="f4aba-135">To Create a Synonym</span></span>  
  
1.  <span data-ttu-id="f4aba-136">[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f4aba-137">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4aba-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f4aba-138">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f4aba-138">Copy and paste the following examples into the query window and click **Execute**.</span></span>  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="f4aba-139">例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="f4aba-139">Example (Transact-SQL)</span></span>  
 <span data-ttu-id="f4aba-140">次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース内の既存のテーブルに対してシノニムを作成します。</span><span class="sxs-lookup"><span data-stu-id="f4aba-140">The following example creates a synonym for an existing table in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="f4aba-141">このシノニムは、その後の例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="f4aba-141">The synonym is then used in subsequent examples.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyAddressType  
FOR AdventureWorks2012.Person.AddressType;  
GO  
```  
  
 <span data-ttu-id="f4aba-142">次の例では、 `MyAddressType` シノニムの参照先のベース テーブルに行を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="f4aba-142">The following example inserts a row into the base table that is referenced by the `MyAddressType` synonym.</span></span>  
  
```  
USE tempdb;  
GO  
INSERT INTO MyAddressType (Name)  
VALUES ('Test');  
GO  
```  
  
 <span data-ttu-id="f4aba-143">次の例では、動的 SQL でのシノニムの参照方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f4aba-143">The following example demonstrates how a synonym can be referenced in dynamic SQL.</span></span>  
  
```  
USE tempdb;  
GO  
EXECUTE ('SELECT Name FROM MyAddressType');  
GO  
```  
  
  
