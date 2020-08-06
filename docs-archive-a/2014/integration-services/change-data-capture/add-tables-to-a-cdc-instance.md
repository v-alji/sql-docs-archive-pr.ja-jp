---
title: CDC へのテーブルの追加 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- addTabs
ms.assetid: ad260e19-c021-4035-9311-c02fc96ceaea
author: chugugrace
ms.author: chugu
ms.openlocfilehash: edcd84db9e3c464334d407987cb3567f78edd44e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712325"
---
# <a name="add-tables-to-a-cdc-instance"></a><span data-ttu-id="58b18-102">CDC へのテーブルの追加</span><span class="sxs-lookup"><span data-stu-id="58b18-102">Add Tables to a CDC Instance</span></span>
  <span data-ttu-id="58b18-103">[テーブル選択] ダイアログ ボックスを使用すると、Oracle ソースから CDC インスタンスに追加のテーブルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="58b18-103">Use the Table Selection dialog box to add additional tables from the Oracle source to the CDC instance.</span></span> <span data-ttu-id="58b18-104">選択したテーブルは、プロパティ エディターの **[テーブル]** タブの一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-104">The tables selected are added to the list in the **Tables** tab of the Properties editor.</span></span>  
  
 <span data-ttu-id="58b18-105">既定では、このダイアログ ボックスのテーブルの一覧にはテーブルが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="58b18-105">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="58b18-106">**[(すべて選択)]** チェック ボックスをオンにするか、特定のテーブルを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="58b18-106">You can select the **(Select All)** check box or search for specific tables.</span></span>  
  
 <span data-ttu-id="58b18-107">**特定のテーブルを検索するには**</span><span class="sxs-lookup"><span data-stu-id="58b18-107">**To search for specific tables**</span></span>  
 <span data-ttu-id="58b18-108">次のように検索条件を入力し、 **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58b18-108">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="58b18-109">**[スキーマ]** : データベース スキーマを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="58b18-109">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="58b18-110">そのスキーマを持つテーブルだけが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-110">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="58b18-111">**[テーブル名パターン]** : 任意の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="58b18-111">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="58b18-112">入力した文字列を含むテーブルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-112">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58b18-113">これらのフィールドの一方または両方に条件を入力できます。</span><span class="sxs-lookup"><span data-stu-id="58b18-113">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="58b18-114">**[一致するテーブルのうち最初の 1000 個を表示する]** : 既定ではこのチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="58b18-114">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="58b18-115">一致するテーブルのうち最初の 1000 個のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-115">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="58b18-116">このチェック ボックスをオフにすると、条件に一致するすべてのテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-116">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="58b18-117">テーブルが多数存在する場合、一覧の表示に時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="58b18-117">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="58b18-118">**CDC インスタンスに含めるテーブルを選択するには**</span><span class="sxs-lookup"><span data-stu-id="58b18-118">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="58b18-119">含めるテーブルの横のチェック ボックスをオンにして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58b18-119">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="58b18-120">新しいインスタンス ウィザードの **[テーブルと列の選択]** ページの一覧にテーブルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="58b18-120">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="58b18-121">テーブルを追加せずにダイアログ ボックスを閉じる場合は、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="58b18-121">Click **Close** to close the dialog box without adding any tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58b18-122">サポートされていないデータ型が含まれているテーブルを選択すると、エラー メッセージが表示され、そのテーブルは追加されません。</span><span class="sxs-lookup"><span data-stu-id="58b18-122">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="58b18-123">テーブルの一覧は、ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="58b18-123">You can view the list of tables in the viewer.</span></span> <span data-ttu-id="58b18-124">ビューアーを使用する場合、情報は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="58b18-124">When using the viewer the information is read only.</span></span> <span data-ttu-id="58b18-125">ビューアーには、テーブルのキャプチャ対象列の一覧も含まれています。</span><span class="sxs-lookup"><span data-stu-id="58b18-125">The viewer also includes a list of the captured columns in the table.</span></span> <span data-ttu-id="58b18-126">ビューアーへのアクセス方法については、「 [How to Manage a CDC Instance](manage-a-cdc-instance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58b18-126">For information on how to access the viewer, see [How to Manage a CDC Instance](manage-a-cdc-instance.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b18-127">参照</span><span class="sxs-lookup"><span data-stu-id="58b18-127">See Also</span></span>  
 <span data-ttu-id="58b18-128">[CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="58b18-128">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 <span data-ttu-id="58b18-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="58b18-129">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="58b18-130">変更をキャプチャするための Oracle テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="58b18-130">Select Oracle Tables for Capturing Changes</span></span>](select-oracle-tables-for-capturing-changes.md)  
  
  
