---
title: '[全般] ([データソースのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c79ad70cdd4dcb10e1abce1102fa39eef4c67461
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631659"
---
# <a name="data-source-properties-dialog-box-general"></a><span data-ttu-id="98e1a-102">[全般] ([データ ソースのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="98e1a-102">Data Source Properties Dialog Box, General</span></span>
  <span data-ttu-id="98e1a-103">**[データ ソースのプロパティ]** ダイアログ ボックスの **[全般]** を選択すると、レポート内のデータ ソースに関する接続情報を表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="98e1a-103">Select **General** on the **Data Source Properties** dialog box to display and modify connection information for a data source in the report.</span></span>  
  
## <a name="options"></a><span data-ttu-id="98e1a-104">Options</span><span class="sxs-lookup"><span data-stu-id="98e1a-104">Options</span></span>  
 <span data-ttu-id="98e1a-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="98e1a-105">**Name**</span></span>  
 <span data-ttu-id="98e1a-106">データ ソースの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-106">Type the name of the data source.</span></span> <span data-ttu-id="98e1a-107">データ ソース名はレポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="98e1a-107">The data source name must be unique within the report.</span></span> <span data-ttu-id="98e1a-108">既定では、DataSource1 または DataSource2 などの一般的な名前がデータ ソースに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="98e1a-108">By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.</span></span>  
  
 <span data-ttu-id="98e1a-109">**[埋め込み接続]**</span><span class="sxs-lookup"><span data-stu-id="98e1a-109">**Embedded connection**</span></span>  
 <span data-ttu-id="98e1a-110">共有データ ソースを使用しない場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-110">Select this option when you do not want to use a shared data source.</span></span>  
  
 <span data-ttu-id="98e1a-111">**Type**</span><span class="sxs-lookup"><span data-stu-id="98e1a-111">**Type**</span></span>  
 <span data-ttu-id="98e1a-112">データ処理拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-112">Select a data processing extension.</span></span> <span data-ttu-id="98e1a-113">一覧には、登録されているすべての拡張機能が表示されます。</span><span class="sxs-lookup"><span data-stu-id="98e1a-113">The list displays all registered extensions.</span></span>  
  
 <span data-ttu-id="98e1a-114">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="98e1a-114">**Connection string**</span></span>  
 <span data-ttu-id="98e1a-115">データ ソースの接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-115">Enter a connection string for the data source.</span></span> <span data-ttu-id="98e1a-116">**[編集]** をクリックして、 **[接続のプロパティ]** ダイアログ ボックスで接続文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-116">Click **Edit** to build the connection string using the **Connection Properties** dialog box.</span></span> <span data-ttu-id="98e1a-117">式を編集するには、 **式** (*[fx]*) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="98e1a-117">Click the **Expressions** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="98e1a-118">**[共有データ ソース参照を使用する]**</span><span class="sxs-lookup"><span data-stu-id="98e1a-118">**Use shared data source reference**</span></span>  
 <span data-ttu-id="98e1a-119">共有データ ソースにリンクする場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-119">Select this option to link to a shared data source.</span></span> <span data-ttu-id="98e1a-120">ドロップダウン リストから共有データ ソースを選択します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-120">Select a shared data source from the drop-down list.</span></span> <span data-ttu-id="98e1a-121">選択したデータ ソースを編集する場合は、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="98e1a-121">To edit the selected data source, click **Edit**.</span></span> <span data-ttu-id="98e1a-122">**[共有データ ソース参照を使用する]** が選択されている場合、 **[型]** および **[接続文字列]** は使用できません。</span><span class="sxs-lookup"><span data-stu-id="98e1a-122">If **Use shared data source reference** is selected, **Type** and **Connection string** are disabled.</span></span>  
  
 <span data-ttu-id="98e1a-123">**[クエリの処理時に単一のトランザクションを使用する]**</span><span class="sxs-lookup"><span data-stu-id="98e1a-123">**Use a single transaction when processing the queries**</span></span>  
 <span data-ttu-id="98e1a-124">このデータ ソースを使用するデータセットが、データベースに対する単一のトランザクションで処理されるように指定する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-124">Select this option to indicate that datasets that use this data source are run in a single transaction against the database.</span></span> <span data-ttu-id="98e1a-125">同じデータ ソースを使用するサブレポートのトランザクションを含めるには、 **[プロパティ]** ペインのサブレポートの **[その他]** のプロパティ セクションで、 **[MergeTransactions]** を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="98e1a-125">To include transactions for subreports that use the same data source, set **MergeTransactions** to **True** in the subreport's **Other** properties section of the **Properties** pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e1a-126">参照</span><span class="sxs-lookup"><span data-stu-id="98e1a-126">See Also</span></span>  
 <span data-ttu-id="98e1a-127">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="98e1a-127">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="98e1a-128">[SSRS&#41;&#40;埋め込みデータソースまたは共有データソースを作成する](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="98e1a-128">[Create an Embedded or Shared Data Source &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md) </span></span>  
 <span data-ttu-id="98e1a-129">[Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="98e1a-129">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="98e1a-130">[[資格情報] ([データ ソースのプロパティ] ダイアログ ボックス)](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="98e1a-130">[Data Source Properties Dialog Box, Credentials](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)</span></span>  
  
  
