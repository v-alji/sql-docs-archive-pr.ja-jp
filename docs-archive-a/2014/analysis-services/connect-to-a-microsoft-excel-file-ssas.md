---
title: Microsoft Excel ファイルへの接続 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.connexcelfile.f1
ms.assetid: 126f7d6b-d270-40e7-b23e-8d114f87065b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79bb3d57470be8acbbb990dde71cf21b62b3cb2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633478"
---
# <a name="connect-to-a-microsoft-excel-file-ssas"></a><span data-ttu-id="b9bae-102">[Microsoft Excel ファイルへの接続] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="b9bae-102">Connect to a Microsoft Excel File (SSAS)</span></span>
  <span data-ttu-id="b9bae-103">**テーブルのインポート ウィザード** のこのページを使用すると、ローカル コンピューターに保存されている Microsoft Excel ファイルに接続できます。</span><span class="sxs-lookup"><span data-stu-id="b9bae-103">This page of the **Table Import Wizard** enables you to connect to a Microsoft Excel file stored on the local machine.</span></span> <span data-ttu-id="b9bae-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b9bae-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="b9bae-105">Microsoft Excel ファイルに接続するには、適切な ACE プロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9bae-105">To connect to a Microsoft Excel file, you must have the appropriate ACE provider installed on your computer.</span></span> <span data-ttu-id="b9bae-106">詳細については、「[サポートされているデータ ソース &#40;SSAS テーブル&#41;](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9bae-106">For more information, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b9bae-107">このページでファイルを選択する際には、現在のユーザーの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9bae-107">The credentials of the current user are used when selecting a file in this page.</span></span> <span data-ttu-id="b9bae-108">ただし、[権限借用情報] ページで指定されたユーザーに、選択したファイルの読み取り権限がないと、インポートは成功しません。</span><span class="sxs-lookup"><span data-stu-id="b9bae-108">However, import will not succeed if the user specified in the Impersonation Information page does not have sufficient privileges to read from the selected file.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="b9bae-109">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="b9bae-109">UI element list</span></span>  
 <span data-ttu-id="b9bae-110">**[接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="b9bae-110">**Friendly connection name**</span></span>  
 <span data-ttu-id="b9bae-111">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b9bae-111">Type a unique name for this data source connection.</span></span> <span data-ttu-id="b9bae-112">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="b9bae-112">This is a required field.</span></span>  
  
 <span data-ttu-id="b9bae-113">**Excel ファイルのパス**</span><span class="sxs-lookup"><span data-stu-id="b9bae-113">**Excel File Path**</span></span>  
 <span data-ttu-id="b9bae-114">Excel ファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9bae-114">Specify a full path for the Excel file.</span></span>  
  
 <span data-ttu-id="b9bae-115">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="b9bae-115">**Browse**</span></span>  
 <span data-ttu-id="b9bae-116">使用可能な Excel ファイルがある場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9bae-116">Navigate to a location where an Excel file is available.</span></span>  
  
 <span data-ttu-id="b9bae-117">**詳細**</span><span class="sxs-lookup"><span data-stu-id="b9bae-117">**Advanced**</span></span>  
 <span data-ttu-id="b9bae-118">**[詳細プロパティの設定**] ダイアログボックスを使用して、追加の接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b9bae-118">Set additional connection properties by using the **Set Advanced Properties** dialog box..</span></span>  
  
 <span data-ttu-id="b9bae-119">**[先頭の行を列見出しとして使用する]**</span><span class="sxs-lookup"><span data-stu-id="b9bae-119">**Use first row as column headers**</span></span>  
 <span data-ttu-id="b9bae-120">先頭のデータ行を目的のテーブルの列見出しとして使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9bae-120">Specify whether to use the first data row as the column headers of the destination table.</span></span>  
  
 <span data-ttu-id="b9bae-121">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="b9bae-121">**Test Connection**</span></span>  
 <span data-ttu-id="b9bae-122">現在の設定を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="b9bae-122">Attempt to establish a connection to the data source using the current settings.</span></span> <span data-ttu-id="b9bae-123">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9bae-123">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
