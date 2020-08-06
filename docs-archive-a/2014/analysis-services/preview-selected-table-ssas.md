---
title: 選択したテーブルのプレビュー (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.previewselecttable.f1
ms.assetid: b6b34b5a-43b3-4a75-9f3b-b2ad1084b1b6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 25eb4d4424223449052ab1f65b41cf270da81fb0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741377"
---
# <a name="preview-selected-table-ssas"></a><span data-ttu-id="34f29-102">[選択したテーブルのプレビュー] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="34f29-102">Preview Selected Table (SSAS)</span></span>
  <span data-ttu-id="34f29-103">**テーブルのインポート ウィザード** のこのページを使用すると、選択したテーブルのデータのプレビュー、データ インポートに含める列の選択、および選択した列のデータのフィルター処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="34f29-103">This page of the **Table Import Wizard** enables you to preview the data in the selected table, to select the columns to include in the data import, and to filter data in the selected columns.</span></span> <span data-ttu-id="34f29-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="34f29-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="34f29-105">テーブルのすべての行が表示されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="34f29-105">Not all the rows in the table are displayed.</span></span> <span data-ttu-id="34f29-106">ただし、設定したフィルターはインポート時にテーブルのすべてのデータに適用されます。</span><span class="sxs-lookup"><span data-stu-id="34f29-106">However, the filters that you set will be applied to all of the data in the table during import.</span></span>  
  
 <span data-ttu-id="34f29-107">Windows 認証を使用したデータ ソースの場合、[プレビューとフィルター] ダイアログに表示されたデータは、現在のユーザーの資格情報を使用してフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="34f29-107">For data sources using Windows authentication, the credentials of the current user are used to fetch the data displayed in the Preview and Filter dialog.</span></span> <span data-ttu-id="34f29-108">その他のデータ ソースについては、接続文字列に指定された資格情報を使用してデータがフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="34f29-108">For other data sources, the credentials supplied in the connection string are used to fetch the data.</span></span>  
  
 <span data-ttu-id="34f29-109">このページに表示されるデータは、インポートの成功を保証するものではありません。</span><span class="sxs-lookup"><span data-stu-id="34f29-109">The appearance of data on this page does not guarantee import will succeed.</span></span> <span data-ttu-id="34f29-110">[権限借用情報] ページで指定されたユーザー名に、選択したデータベースの読み取り権限がないと、インポートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="34f29-110">If the user name specified in the Impersonation Information page does not have sufficient privileges to read from the selected database, import will fail.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="34f29-111">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="34f29-111">UI element list</span></span>  
 <span data-ttu-id="34f29-112">**列ヘッダーのチェック ボックス**</span><span class="sxs-lookup"><span data-stu-id="34f29-112">**Checkbox in the column header**</span></span>  
 <span data-ttu-id="34f29-113">列をデータ インポートの対象にする場合は、チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="34f29-113">Select the checkbox to include the column in the data import.</span></span> <span data-ttu-id="34f29-114">列をデータ インポートの対象から除外する場合は、チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="34f29-114">Clear the checkbox to remove the column from the data import.</span></span>  
  
 <span data-ttu-id="34f29-115">**列ヘッダーの下矢印ボタン**</span><span class="sxs-lookup"><span data-stu-id="34f29-115">**Down-arrow button in the column header**</span></span>  
 <span data-ttu-id="34f29-116">列のデータをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="34f29-116">Filter data in the column.</span></span>  
  
 <span data-ttu-id="34f29-117">**[行フィルターのクリア]**</span><span class="sxs-lookup"><span data-stu-id="34f29-117">**Clear Row Filters**</span></span>  
 <span data-ttu-id="34f29-118">列のデータに適用されているすべてのフィルターを削除します。</span><span class="sxs-lookup"><span data-stu-id="34f29-118">Remove all filters that were applied to the data in the columns.</span></span>  
  
  
