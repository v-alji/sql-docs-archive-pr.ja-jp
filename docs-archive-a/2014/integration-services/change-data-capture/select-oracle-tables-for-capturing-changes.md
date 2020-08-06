---
title: 変更をキャプチャするための Oracle テーブルの選択 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- selOraTabDia
ms.assetid: 2e295dc8-999d-4c4d-96cc-1519674b47a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e9064789dce83ff7d3917ed026c861743142e048
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720301"
---
# <a name="select-oracle-tables-for-capturing-changes"></a><span data-ttu-id="fc0fa-102">変更をキャプチャするための Oracle テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="fc0fa-102">Select Oracle Tables for Capturing Changes</span></span>
  <span data-ttu-id="fc0fa-103">このダイアログ ボックスを使用すると、CDC インスタンスに含めるテーブルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-103">Use this dialog box to select the tables that are included in the CDC instance.</span></span> <span data-ttu-id="fc0fa-104">選択したテーブルは、新しいインスタンス ウィザードの **[テーブルと列の選択]** ページの一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-104">The tables selected are added to the list in the **Select Tables and Columns** page of the New Instance wizard.</span></span> <span data-ttu-id="fc0fa-105">このダイアログ ボックスでは次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-105">You can do the following in this dialog box.</span></span>  
  
 <span data-ttu-id="fc0fa-106">既定では、このダイアログ ボックスのテーブルの一覧にはテーブルが含まれていません。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-106">By default, no tables are included in the list of tables in this dialog box.</span></span> <span data-ttu-id="fc0fa-107">チェック ボックス列の最上部にあるチェック ボックスをオンにしてすべてのテーブルを選択するか、特定のテーブルを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-107">You can select the check box at the top of the check box column to select all of the tables or search for specific tables.</span></span>  
  
 <span data-ttu-id="fc0fa-108">**特定のテーブルを検索するには**</span><span class="sxs-lookup"><span data-stu-id="fc0fa-108">**To search for specific tables**</span></span>  
 <span data-ttu-id="fc0fa-109">次のように検索条件を入力し、 **[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-109">Enter search criteria as follows, and then click **Search**:</span></span>  
  
-   <span data-ttu-id="fc0fa-110">**[スキーマ]** : データベース スキーマを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-110">**Schema**: Select a database schema from the list.</span></span> <span data-ttu-id="fc0fa-111">そのスキーマを持つテーブルだけが一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-111">Only tables that have that schema will be included in the list.</span></span>  
  
-   <span data-ttu-id="fc0fa-112">**[テーブル名パターン]** : 任意の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-112">**Table Name Pattern**: Enter any string of characters.</span></span> <span data-ttu-id="fc0fa-113">入力した文字列を含むテーブルのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-113">Only tables that include the character string entered are displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc0fa-114">これらのフィールドの一方または両方に条件を入力できます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-114">You can enter criteria in one or both of these fields.</span></span>  
  
-   <span data-ttu-id="fc0fa-115">**[一致するテーブルのうち最初の 1000 個を表示する]** : 既定ではこのチェック ボックスはオンになっています。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-115">**Display first 1000 matching tables**: By default this check box is selected.</span></span> <span data-ttu-id="fc0fa-116">一致するテーブルのうち最初の 1000 個のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-116">It limits the display to the first 1000 matching tables.</span></span> <span data-ttu-id="fc0fa-117">このチェック ボックスをオフにすると、条件に一致するすべてのテーブルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-117">If you clear the check box, all tables that match the criteria are displayed.</span></span> <span data-ttu-id="fc0fa-118">テーブルが多数存在する場合、一覧の表示に時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-118">If there are a large number of tables, it may take a long time to display the list.</span></span>  
  
 <span data-ttu-id="fc0fa-119">**CDC インスタンスに含めるテーブルを選択するには**</span><span class="sxs-lookup"><span data-stu-id="fc0fa-119">**To select tables to include in the CDC instance**</span></span>  
 <span data-ttu-id="fc0fa-120">含めるテーブルの横のチェック ボックスをオンにして、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-120">Click the check box next to any of the tables you want to include, and then click **Add**.</span></span> <span data-ttu-id="fc0fa-121">新しいインスタンス ウィザードの **[テーブルと列の選択]** ページの一覧にテーブルが追加されます。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-121">The tables are added to the list in the New Instance Wizard **Select Tables and Columns** page.</span></span>  
  
 <span data-ttu-id="fc0fa-122">その他のテーブルを追加せずにダイアログ ボックスを閉じる場合は、 **[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-122">Click **Close** to close the dialog box without adding any additional tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fc0fa-123">サポートされていないデータ型が含まれているテーブルを選択すると、エラー メッセージが表示され、そのテーブルは追加されません。</span><span class="sxs-lookup"><span data-stu-id="fc0fa-123">If you select a table that includes a non-supported data type, you will see an error message and the table will not be included.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0fa-124">参照</span><span class="sxs-lookup"><span data-stu-id="fc0fa-124">See Also</span></span>  
 <span data-ttu-id="fc0fa-125">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="fc0fa-125">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="fc0fa-126">Oracle のテーブルおよび列の選択</span><span class="sxs-lookup"><span data-stu-id="fc0fa-126">Select Oracle Tables and Columns</span></span>](select-oracle-tables-and-columns.md)  
  
  
