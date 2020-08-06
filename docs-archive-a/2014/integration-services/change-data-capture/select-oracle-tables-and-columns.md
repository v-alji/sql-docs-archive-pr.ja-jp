---
title: Oracle のテーブルおよび列の選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selTabCol
ms.assetid: bf73f80e-a954-4c5f-874e-17fdd4082715
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d51e597f1210643b1543ed981045ade7b2fc2b62
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634586"
---
# <a name="select-oracle-tables-and-columns"></a><span data-ttu-id="d2ad5-102">Oracle のテーブルおよび列の選択</span><span class="sxs-lookup"><span data-stu-id="d2ad5-102">Select Oracle Tables and Columns</span></span>
  <span data-ttu-id="d2ad5-103">[Oracle のテーブルおよび列の選択] ページを使用すると、変更をキャプチャする Oracle ソース データベースからテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-103">Use the Select Oracle Tables and Columns page to select the tables from the Oracle source database where changes are captured.</span></span> <span data-ttu-id="d2ad5-104">このページには次の要素があります。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-104">This page has the following elements:</span></span>  
  
## <a name="options"></a><span data-ttu-id="d2ad5-105">オプション</span><span class="sxs-lookup"><span data-stu-id="d2ad5-105">Options</span></span>  
 <span data-ttu-id="d2ad5-106">**テーブルの一覧**</span><span class="sxs-lookup"><span data-stu-id="d2ad5-106">**Table list**</span></span>  
 <span data-ttu-id="d2ad5-107">テーブルの一覧には、次の 3 列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-107">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="d2ad5-108">**[Oracle テーブル名]** : テーブル スキーマを含むテーブルの名前です。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-108">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="d2ad5-109">**[キャプチャ インスタンス]** : インスタンス固有の変更データ キャプチャ オブジェクトを識別するために使用されるキャプチャ インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-109">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="d2ad5-110">キャプチャ インスタンスは NULL にできません。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-110">The capture instance cannot be NULL.</span></span>  
  
     <span data-ttu-id="d2ad5-111">指定しない場合、ソース スキーマ名とソース テーブル名に基づき、 `<schema-name>_<table-name>`形式の名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-111">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>`.</span></span> <span data-ttu-id="d2ad5-112">キャプチャ インスタンス名は 100 文字を超えることはできず、データベース内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-112">The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span>  
  
     <span data-ttu-id="d2ad5-113">この列のセルをクリックすると、 **capture_instance**を手動で編集できます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-113">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="d2ad5-114">**[セキュリティ ロール]** : 変更データへのアクセスを制御するために使用されるデータベースのゲーティング ロールの名前です。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-114">**Security Role**: The name of the database gating role used to control access to change data.</span></span>  
  
     <span data-ttu-id="d2ad5-115">この列のセルをクリックすると、 **security_role**を手動で編集できます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-115">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="d2ad5-116">**テーブルの追加**</span><span class="sxs-lookup"><span data-stu-id="d2ad5-116">**Add Tables**</span></span>  
 <span data-ttu-id="d2ad5-117">**[テーブルの追加]** をクリックすると、 [変更をキャプチャするための Oracle テーブルの選択](select-oracle-tables-for-capturing-changes.md)を行うことができる [テーブル選択] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-117">Click **Add Tables** to open the Table Selection dialog box where you can [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="d2ad5-118">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="d2ad5-118">**Edit**</span></span>  
 <span data-ttu-id="d2ad5-119">一覧からテーブルを選択して **[編集]** をクリックすると、そのテーブルの **[プロパティ]** ダイアログ ボックスが表示され、 [変更をキャプチャするために選択したテーブルに対する変更](make-changes-to-the-tables-selected-for-capturing-changes.md)を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-119">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md).</span></span>  
  
 <span data-ttu-id="d2ad5-120">**Remove**</span><span class="sxs-lookup"><span data-stu-id="d2ad5-120">**Remove**</span></span>  
 <span data-ttu-id="d2ad5-121">一覧からテーブルを選択して **[削除]** をクリックすると、CDC インスタンスからテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-121">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
 <span data-ttu-id="d2ad5-122">適切なダイアログ ボックスを使用して [変更をキャプチャするための Oracle テーブルの選択](select-oracle-tables-for-capturing-changes.md) または [変更をキャプチャするために選択したテーブルに対する変更](make-changes-to-the-tables-selected-for-capturing-changes.md) を行った後、 **[次へ]** をクリックして [補足ログ スクリプトの生成および実行](generate-and-run-the-supplemental-logging-script.md)を行います。</span><span class="sxs-lookup"><span data-stu-id="d2ad5-122">After you [Select Oracle Tables for Capturing Changes](select-oracle-tables-for-capturing-changes.md) and/or [Make Changes to the Tables Selected for Capturing Changes](make-changes-to-the-tables-selected-for-capturing-changes.md) using the correct dialog boxes, click **Next** to [Generate and Run the Supplemental Logging Script](generate-and-run-the-supplemental-logging-script.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ad5-123">参照</span><span class="sxs-lookup"><span data-stu-id="d2ad5-123">See Also</span></span>  
 <span data-ttu-id="d2ad5-124">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d2ad5-124">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 <span data-ttu-id="d2ad5-125">[テーブルの編集](edit-tables.md) </span><span class="sxs-lookup"><span data-stu-id="d2ad5-125">[Edit Tables](edit-tables.md) </span></span>  
 <span data-ttu-id="d2ad5-126">[CDC へのテーブルの追加](add-tables-to-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="d2ad5-126">[Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="d2ad5-127">テーブルのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="d2ad5-127">Edit the Table Properties</span></span>](edit-the-table-properties.md)  
  
  
