---
title: 接続文字列を指定する (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.speconnstring.f1
ms.assetid: 3f89b55b-2659-4e9f-a3ad-ab9a23b6942d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9333c239504a79184e08776acb3f1d845f06cc4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736853"
---
# <a name="specify-a-connection-string-ssas"></a><span data-ttu-id="ceae0-102">[接続文字列の指定] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="ceae0-102">Specify a connection string (SSAS)</span></span>
  <span data-ttu-id="ceae0-103">**テーブルのインポート ウィザード** のこのページを使用すると、OLE DB データ ソースまたは ODBC データ ソースに接続するための接続文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ceae0-103">This page of the **Table Import Wizard** enables you to specify a connection string to connect to an OLE DB or ODBC data source.</span></span> <span data-ttu-id="ceae0-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ceae0-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
 <span data-ttu-id="ceae0-105">データ ソースに接続するには、適切なプロバイダーがコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceae0-105">To connect to a data source, you must have the appropriate provider installed on your computer.</span></span> <span data-ttu-id="ceae0-106">サポートされているデータ ソースおよびプロバイダーの詳細については、「 [サポートされているデータ ソース (SSAS テーブル)](tabular-models/data-sources-supported-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ceae0-106">For more information about supported data sources and providers, see [Data Sources Supported &#40;SSAS Tabular&#41;](tabular-models/data-sources-supported-ssas-tabular.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="ceae0-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="ceae0-107">UI element list</span></span>  
 <span data-ttu-id="ceae0-108">**[この接続の表示名]**</span><span class="sxs-lookup"><span data-stu-id="ceae0-108">**Friendly name for this connection**</span></span>  
 <span data-ttu-id="ceae0-109">このデータ ソース接続の一意の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="ceae0-109">Type a unique name for this data source connection.</span></span> <span data-ttu-id="ceae0-110">これは必須フィールドです。</span><span class="sxs-lookup"><span data-stu-id="ceae0-110">This is a required field.</span></span>  
  
 <span data-ttu-id="ceae0-111">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="ceae0-111">**Connection String**</span></span>  
 <span data-ttu-id="ceae0-112">OLE DB または ODBC データ ソースへの接続に使用する接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="ceae0-112">Type a connection string to connect to an OLE DB or ODBC data source.</span></span>  
  
 <span data-ttu-id="ceae0-113">**ビルド**</span><span class="sxs-lookup"><span data-stu-id="ceae0-113">**Build**</span></span>  
 <span data-ttu-id="ceae0-114">**[データ リンク プロパティ]** ダイアログ ボックスを使用して接続文字列のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="ceae0-114">Specify the properties for a connection string by using the **Data Link Properties** dialog box.</span></span> <span data-ttu-id="ceae0-115">詳細については、Microsoft Data Link のヘルプを参照してください。このダイアログ ボックスから参照できます。</span><span class="sxs-lookup"><span data-stu-id="ceae0-115">For more information, see the Microsoft Data Link Help, which is available from that dialog box.</span></span>  
  
 <span data-ttu-id="ceae0-116">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="ceae0-116">**Test Connection**</span></span>  
 <span data-ttu-id="ceae0-117">指定された接続文字列を使用して、データ ソースに対する接続の確立を試みます。</span><span class="sxs-lookup"><span data-stu-id="ceae0-117">Attempt to establish a connection to the data source using the specified connection string.</span></span> <span data-ttu-id="ceae0-118">接続が正常に確立されたかどうかを示すメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ceae0-118">A message is displayed indicating whether the connection is successful.</span></span>  
  
  
