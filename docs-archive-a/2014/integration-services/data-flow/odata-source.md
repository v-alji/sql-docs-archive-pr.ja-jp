---
title: OData ソース | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 98b14ef034597f6098f70386ca41c1b90be86500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741138"
---
# <a name="odata-source"></a><span data-ttu-id="01279-102">OData ソース</span><span class="sxs-lookup"><span data-stu-id="01279-102">OData Source</span></span>
  <span data-ttu-id="01279-103">SSIS パッケージ内で OData ソース コンポーネントを使用して、Open Data Protocol (OData) サービスから取得したデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="01279-103">You use the OData Source component in an SSIS package to consume data from Open Data Protocol (OData) services.</span></span> <span data-ttu-id="01279-104">このコンポーネントは、OData v2 と v3 の各プロトコル、および ATOM と JSON の各データ形式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="01279-104">The component supports the OData v2 and v3 protocols, as well as the ATOM and JSON data formats.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="01279-105">OData ソースを使用して、SharePoint リストから読み取りを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="01279-105">The OData Source can be used to read from SharePoint lists.</span></span> <span data-ttu-id="01279-106">SharePoint サーバー上のすべてのリストを表示するには、次の URL を使用します: http:// \<server> /_vti_bin/listdata.svc.</span><span class="sxs-lookup"><span data-stu-id="01279-106">To see all lists on your SharePoint server, use the following URL: http://\<server>/_vti_bin/ListData.svc.</span></span> <span data-ttu-id="01279-107">SharePoint の URL の規則に関する詳細については、「 [SharePoint Foundation REST インターフェイス](https://msdn.microsoft.com/library/ff521587.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01279-107">For more information about SharePoint URL conventions, see [SharePoint Foundation REST Interface](https://msdn.microsoft.com/library/ff521587.aspx).</span></span>  
  
## <a name="odata-format"></a><span data-ttu-id="01279-108">OData の形式</span><span class="sxs-lookup"><span data-stu-id="01279-108">OData Format</span></span>  
 <span data-ttu-id="01279-109">ほとんどの OData サービスは、結果を複数の形式で返します。</span><span class="sxs-lookup"><span data-stu-id="01279-109">Most OData services return results in multiple formats.</span></span> <span data-ttu-id="01279-110">$format クエリ オプションを使用して、結果セットの形式を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="01279-110">You can specify the format of the result set by using the $format query option.</span></span> <span data-ttu-id="01279-111">JSON と JSON Light のような形式は、ATOM/XML より効率的であり、大量のデータを転送する場合により高いパフォーマンスを達成できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01279-111">Formats such as JSON and JSON Light are more efficient than ATOM/XML, and may give you better performance when transferring large amounts of data.</span></span> <span data-ttu-id="01279-112">次の表に、サンプル テストの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="01279-112">The following table provides results from sample tests.</span></span> <span data-ttu-id="01279-113">ご覧のように、atom から 67 JSON に切り替えるとパフォーマンスが30-53% 向上し、ATOM から新しい JSON light 形式 (WCF Data Services 5.1 で利用可能) に切り替えるとパフォーマンスが向上しました。</span><span class="sxs-lookup"><span data-stu-id="01279-113">As you can see, there was a 30-53% performance gain when switching from ATOM to JSON and 67% performance gain when switching from ATOM to the new JSON light format (available in WCF Data Services 5.1).</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="01279-114">[行]</span><span class="sxs-lookup"><span data-stu-id="01279-114">Rows</span></span>|<span data-ttu-id="01279-115">ATOM</span><span class="sxs-lookup"><span data-stu-id="01279-115">ATOM</span></span>|<span data-ttu-id="01279-116">JSON</span><span class="sxs-lookup"><span data-stu-id="01279-116">JSON</span></span>|<span data-ttu-id="01279-117">JSON (Light)</span><span class="sxs-lookup"><span data-stu-id="01279-117">JSON (Light)</span></span>|  
|<span data-ttu-id="01279-118">10000</span><span class="sxs-lookup"><span data-stu-id="01279-118">10000</span></span>|<span data-ttu-id="01279-119">113 秒</span><span class="sxs-lookup"><span data-stu-id="01279-119">113 seconds</span></span>|<span data-ttu-id="01279-120">74 秒</span><span class="sxs-lookup"><span data-stu-id="01279-120">74 seconds</span></span>|<span data-ttu-id="01279-121">68 秒</span><span class="sxs-lookup"><span data-stu-id="01279-121">68 seconds</span></span>|  
|<span data-ttu-id="01279-122">1000000</span><span class="sxs-lookup"><span data-stu-id="01279-122">1000000</span></span>|<span data-ttu-id="01279-123">1110 秒</span><span class="sxs-lookup"><span data-stu-id="01279-123">1110 seconds</span></span>|<span data-ttu-id="01279-124">853 秒</span><span class="sxs-lookup"><span data-stu-id="01279-124">853 seconds</span></span>|<span data-ttu-id="01279-125">665 秒</span><span class="sxs-lookup"><span data-stu-id="01279-125">665 seconds</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="01279-126">SSIS OData ソースは、ODataLib 5.5.0 を使用して OData フィードを分析し、このライブラリでサポートされているすべてのフォーマットを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="01279-126">The SSIS OData Source uses ODataLib 5.5.0 to parse OData feeds and it can read all formats supported by this library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="01279-127">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="01279-127">In This Section</span></span>  
  
-   [<span data-ttu-id="01279-128">OData ソース コンポーネントのインストールと、アンインストール</span><span class="sxs-lookup"><span data-stu-id="01279-128">Install and Uninstall OData Source Component</span></span>](../install-and-uninstall-odata-source-component.md)  
  
-   [<span data-ttu-id="01279-129">チュートリアル: OData ソース &#91;SSIS&#93;の使用</span><span class="sxs-lookup"><span data-stu-id="01279-129">Tutorial: Using the OData Source &#91;SSIS&#93;</span></span>](tutorial-using-the-odata-source.md)  
  
-   [<span data-ttu-id="01279-130">実行時の OData ソース クエリの変更</span><span class="sxs-lookup"><span data-stu-id="01279-130">Modify OData Source Query at Runtime</span></span>](modify-odata-source-query-at-runtime.md)  
  
-   <span data-ttu-id="01279-131">[[OData ソース エディター] &#40;[接続] ページ&#41;](../odata-source-editor-connection-page.md)</span><span class="sxs-lookup"><span data-stu-id="01279-131">[OData Source Editor &#40;Connection Page&#41;](../odata-source-editor-connection-page.md)</span></span>  
  
-   <span data-ttu-id="01279-132">[OData ソース エディター ([列] ページ)](../odata-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="01279-132">[OData Source Editor &#40;Columns Page&#41;](../odata-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="01279-133">[OData ソース エディター &#40;[エラー出力] ページ&#41;](../odata-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="01279-133">[OData Source Editor &#40;Error Output Page&#41;](../odata-source-editor-error-output-page.md)</span></span>  
  
-   [<span data-ttu-id="01279-134">OData ソースのプロパティ</span><span class="sxs-lookup"><span data-stu-id="01279-134">OData Source Properties</span></span>](odata-source-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="01279-135">参照</span><span class="sxs-lookup"><span data-stu-id="01279-135">See Also</span></span>  
 [<span data-ttu-id="01279-136">OData 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="01279-136">OData Connection Manager</span></span>](../connection-manager/odata-connection-manager.md)  
  
  
