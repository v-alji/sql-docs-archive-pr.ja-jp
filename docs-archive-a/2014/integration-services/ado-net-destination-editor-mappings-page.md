---
title: '[ADO NET 変換先エディター] ([マッピング] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.adonetdest.mappings.f1
ms.assetid: 842d075f-8b7a-457c-a1a1-a7acbe10e9b7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7e7a2397e4e2d16e6eeca93d41f5127dfde4c35e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631207"
---
# <a name="ado-net-destination-editor-mappings-page"></a><span data-ttu-id="9aa39-102">[ADO NET 変換先エディター] ([マッピング] ページ)</span><span class="sxs-lookup"><span data-stu-id="9aa39-102">ADO NET Destination Editor (Mappings Page)</span></span>
  <span data-ttu-id="9aa39-103">**[ADO NET 変換先エディター]** ダイアログ ボックスの **[マッピング]** ページを使用すると、入力列を変換先列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="9aa39-103">Use the **Mappings** page of the **ADO NET Destination Editor** dialog box to map input columns to destination columns.</span></span>  
  
 <span data-ttu-id="9aa39-104">ADO NET 変換先の詳細については、「 [ADO NET Destination](data-flow/ado-net-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9aa39-104">To learn more about the ADO NET destination, see [ADO NET Destination](data-flow/ado-net-destination.md).</span></span>  
  
 <span data-ttu-id="9aa39-105">**[マッピング] ページを開くには**</span><span class="sxs-lookup"><span data-stu-id="9aa39-105">**To open the Mappings page**</span></span>  
  
1.  <span data-ttu-id="9aa39-106">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換先を含む [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="9aa39-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package that has the ADO NET destination.</span></span>  
  
2.  <span data-ttu-id="9aa39-107">**[データ フロー]** タブで、ADO NET 変換先をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9aa39-107">On the **Data Flow** tab, double-click the ADO NET destination.</span></span>  
  
3.  <span data-ttu-id="9aa39-108">**[ADO NET 変換先エディター]** で、 **[マッピング]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9aa39-108">In the **ADO NET Destination Editor**, click **Mappings**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9aa39-109">Options</span><span class="sxs-lookup"><span data-stu-id="9aa39-109">Options</span></span>  
 <span data-ttu-id="9aa39-110">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="9aa39-110">**Available Input Columns**</span></span>  
 <span data-ttu-id="9aa39-111">使用できる入力列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9aa39-111">View the list of available input columns.</span></span> <span data-ttu-id="9aa39-112">ドラッグ アンド ドロップ操作により、テーブル内の使用できる入力列を変換先列にマップします。</span><span class="sxs-lookup"><span data-stu-id="9aa39-112">Use a drag-and-drop operation to map available input columns in the table to destination columns.</span></span>  
  
 <span data-ttu-id="9aa39-113">**使用できる変換先列**</span><span class="sxs-lookup"><span data-stu-id="9aa39-113">**Available Destination Columns**</span></span>  
 <span data-ttu-id="9aa39-114">使用できる変換先列の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="9aa39-114">View the list of available destination columns.</span></span> <span data-ttu-id="9aa39-115">ドラッグ アンド ドロップ操作により、テーブル内の使用できる変換先列を入力列にマップします。</span><span class="sxs-lookup"><span data-stu-id="9aa39-115">Use a drag-and-drop operation to map available destination columns in the table to input columns.</span></span>  
  
 <span data-ttu-id="9aa39-116">**入力列**</span><span class="sxs-lookup"><span data-stu-id="9aa39-116">**Input Column**</span></span>  
 <span data-ttu-id="9aa39-117">選択した入力列を表示します。</span><span class="sxs-lookup"><span data-stu-id="9aa39-117">View the input columns that you selected.</span></span> <span data-ttu-id="9aa39-118">出力から列を除外するために **[\<ignore>]** を選択することで、マッピングを削除できます。</span><span class="sxs-lookup"><span data-stu-id="9aa39-118">You can remove mappings by selecting **\<ignore>** to exclude columns from the output.</span></span>  
  
 <span data-ttu-id="9aa39-119">**変換先列**</span><span class="sxs-lookup"><span data-stu-id="9aa39-119">**Destination Column**</span></span>  
 <span data-ttu-id="9aa39-120">マップするかどうかにかかわらず、使用できる変換先列を表示します。</span><span class="sxs-lookup"><span data-stu-id="9aa39-120">View each available destination column, regardless of whether it is mapped or not.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa39-121">参照</span><span class="sxs-lookup"><span data-stu-id="9aa39-121">See Also</span></span>  
 <span data-ttu-id="9aa39-122">[[ADO NET 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span><span class="sxs-lookup"><span data-stu-id="9aa39-122">[ADO NET Destination Editor &#40;Connection Manager Page&#41;](../../2014/integration-services/ado-net-destination-editor-connection-manager-page.md) </span></span>  
 <span data-ttu-id="9aa39-123">[[ADO NET 変換先エディター] &#40;[エラー出力] ページ&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="9aa39-123">[ADO NET Destination Editor &#40;Error Output Page&#41;](../../2014/integration-services/ado-net-destination-editor-error-output-page.md)</span></span>  
  
  
