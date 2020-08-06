---
title: テーブルの編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- tabProps
ms.assetid: fed8fada-2abc-45e2-8228-0656f9c599cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8e8058a0c3e8b81814283f055e4c4ac2b08dd2fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632045"
---
# <a name="edit-tables"></a><span data-ttu-id="8ae48-102">テーブルの編集</span><span class="sxs-lookup"><span data-stu-id="8ae48-102">Edit Tables</span></span>
  <span data-ttu-id="8ae48-103">Oracle ソース データベースから選択したテーブルおよび列を変更するには、 **[テーブル]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ae48-103">Use the **Tables** tab to make changes to the tables and columns that you selected from the Oracle source database.</span></span> <span data-ttu-id="8ae48-104">このタブには次の要素があります。</span><span class="sxs-lookup"><span data-stu-id="8ae48-104">This tab has the following elements:</span></span>  
  
 <span data-ttu-id="8ae48-105">**テーブルの一覧**</span><span class="sxs-lookup"><span data-stu-id="8ae48-105">**Table list**</span></span>  
 <span data-ttu-id="8ae48-106">テーブルの一覧には、次の 3 列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ae48-106">The table list has three columns:</span></span>  
  
-   <span data-ttu-id="8ae48-107">**[Oracle テーブル名]** : テーブル スキーマを含むテーブルの名前です。</span><span class="sxs-lookup"><span data-stu-id="8ae48-107">**Oracle Table Name**: The name of the table, including the table schema.</span></span>  
  
-   <span data-ttu-id="8ae48-108">**[キャプチャ インスタンス]** : インスタンス固有の変更データ キャプチャ オブジェクトを識別するために使用されるキャプチャ インスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="8ae48-108">**Capture Instance**: The name of the capture instance used to name instance-specific change data capture objects.</span></span> <span data-ttu-id="8ae48-109">キャプチャ インスタンスは NULL にできません。</span><span class="sxs-lookup"><span data-stu-id="8ae48-109">The capture instance cannot be NULL.</span></span> <span data-ttu-id="8ae48-110">指定しなかった場合、ソース スキーマ名とソース テーブル名に基づいて、 `<schema-name>_<table-name>.` 形式の名前が付けられます。キャプチャ インスタンスの名前に指定できる文字数の上限は 100 文字です。また、データベース内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="8ae48-110">If not specified, the name is derived from the source schema name plus the source table name in the format `<schema-name>_<table-name>.` The capture instance name cannot exceed 100 characters and must be unique within the database.</span></span> <span data-ttu-id="8ae48-111">この列のセルをクリックすると、 **capture_instance**を手動で編集できます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-111">You can click in any cell in this column to manually edit the **capture_instance**.</span></span>  
  
-   <span data-ttu-id="8ae48-112">**[セキュリティ ロール]** : 変更データへのアクセスの取得に使用するデータベース ロールの名前です。</span><span class="sxs-lookup"><span data-stu-id="8ae48-112">**Security Role**: The name of the database role used to gain access to change data.</span></span> <span data-ttu-id="8ae48-113">この列のセルをクリックすると、 **security_role**を手動で編集できます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-113">You can click in any cell in this column to manually edit the **security_role**.</span></span>  
  
 <span data-ttu-id="8ae48-114">**テーブルの追加**</span><span class="sxs-lookup"><span data-stu-id="8ae48-114">**Add Tables**</span></span>  
 <span data-ttu-id="8ae48-115">**[テーブルの追加]** をクリックすると、 [CDC へのテーブルの追加](add-tables-to-a-cdc-instance.md)を行うことができる [テーブル選択] ダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-115">Click **Add Tables** to open the Table Selection dialog box where you can [Add Tables to a CDC Instance](add-tables-to-a-cdc-instance.md).</span></span> <span data-ttu-id="8ae48-116">このセッションが Oracle データベースへの初回のアクセスである場合、 [Connect to Oracle](connect-to-oracle.md)を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ae48-116">The first time this session that you access the Oracle database, you must [Connect to Oracle](connect-to-oracle.md).</span></span>  
  
 <span data-ttu-id="8ae48-117">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="8ae48-117">**Edit**</span></span>  
 <span data-ttu-id="8ae48-118">一覧からテーブルを選択して **[編集]** をクリックすると、そのテーブルの **[プロパティ]** ダイアログ ボックスが表示され、 [テーブルのプロパティの編集](edit-the-table-properties.md)を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-118">Select a table from the list and select **Edit** to open the **Properties** dialog box for that table where you can [Edit the Table Properties](edit-the-table-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8ae48-119">既にミラー テーブルがあるテーブルの型マッピングは編集できません。</span><span class="sxs-lookup"><span data-stu-id="8ae48-119">You cannot edit type mapping for tables that already have mirror tables.</span></span> <span data-ttu-id="8ae48-120">型マッピングは新しいテーブルに対してのみ行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-120">You can do this for new tables only.</span></span>  
  
 <span data-ttu-id="8ae48-121">**Remove**</span><span class="sxs-lookup"><span data-stu-id="8ae48-121">**Remove**</span></span>  
 <span data-ttu-id="8ae48-122">一覧からテーブルを選択して **[削除]** をクリックすると、CDC インスタンスからテーブルを削除できます。</span><span class="sxs-lookup"><span data-stu-id="8ae48-122">Select a table from the list and click **Remove** to remove the table from the CDC instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ae48-123">参照</span><span class="sxs-lookup"><span data-stu-id="8ae48-123">See Also</span></span>  
 <span data-ttu-id="8ae48-124">[CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="8ae48-124">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="8ae48-125">Oracle のテーブルおよび列の選択</span><span class="sxs-lookup"><span data-stu-id="8ae48-125">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
