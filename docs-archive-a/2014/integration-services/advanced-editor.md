---
title: '[詳細エディター] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.advancededitor.columnmappings.f1
- sql12.dts.designer.advancededitor.inputcolumns.f1
- sql12.dts.designer.advancededitor.columnproperties.f1
- sql12.dts.designer.advancededitor.componentproperties.f1
- sql12.dts.designer.advancededitor.connections.f1
ms.assetid: 5ad0ac71-fa8b-4c26-bd42-e6ef00c87571
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f4897f2589acdeb93efecbdf9aacde07d21ca42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633991"
---
# <a name="advanced-editor"></a><span data-ttu-id="e5c69-102">[詳細エディター]</span><span class="sxs-lookup"><span data-stu-id="e5c69-102">Advanced Editor</span></span>
  <span data-ttu-id="e5c69-103">**[詳細エディター]** ダイアログ ボックスを使用すると、選択した [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトのプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e5c69-103">Use the **Advanced Editor** dialog box to configure to configure properties for the selected [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] object.</span></span>  
  
 <span data-ttu-id="e5c69-104">**[詳細エディター]** は、構成可能なプロパティを持つほとんどの [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] オブジェクトで利用可能です。</span><span class="sxs-lookup"><span data-stu-id="e5c69-104">The **Advanced Editor** is available for most [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] objects that have configurable properties.</span></span> <span data-ttu-id="e5c69-105">カスタム ユーザー インターフェイスを公開しないオブジェクトに対しては、唯一の利用可能なエディターです。</span><span class="sxs-lookup"><span data-stu-id="e5c69-105">It is the only editor available for those objects that do not expose a custom user interface.</span></span>  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="e5c69-106">データ フロー オブジェクトには、コンポーネント レベル、入出力レベル、入力列レベルおよび出力列レベルで設定できるプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e5c69-106">data flow objects have properties that can be set at the component level, the input and output level, and the input and output column level.</span></span> <span data-ttu-id="e5c69-107">**[詳細エディター]** では、選択したオブジェクトの共通のプロパティおよびカスタム プロパティがすべて列挙され、使用可能な次の 5 つのタブのうち 4 つが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e5c69-107">The **Advanced Editor** enumerates all the common and custom properties of the selected object and displays them on up to four of the following five tabs as applicable:</span></span>  
  
-   <span data-ttu-id="e5c69-108">**[接続マネージャー]** : このタブを使用して、接続プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e5c69-108">**Connection Managers** -- use this tab to set connection properties</span></span>  
  
-   <span data-ttu-id="e5c69-109">**[コンポーネントのプロパティ]** : このタブを使用して、コンポーネントレベルのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e5c69-109">**Component Properties** -- use this tab to set component-level properties</span></span>  
  
-   <span data-ttu-id="e5c69-110">**[列マッピング]** : このタブを使用して、使用可能な列を出力列としてマップします。</span><span class="sxs-lookup"><span data-stu-id="e5c69-110">**Column Mappings** -- use this tab to map available columns as output columns</span></span>  
  
-   <span data-ttu-id="e5c69-111">**[入力列]** : このタブを使用して、入力列を選択します。</span><span class="sxs-lookup"><span data-stu-id="e5c69-111">**Input Columns** -- use this tab to select input columns</span></span>  
  
-   <span data-ttu-id="e5c69-112">**[入力プロパティと出力プロパティ]** : このタブを使用して、入力プロパティと出力プロパティを設定します。出力の追加と削除、入力および出力に使用する列の選択と削除、入力および出力のプロパティの設定を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="e5c69-112">**Input and Output Properties** -- use this tab to set input and output properties; and to add and remove outputs, select or remove columns for inputs and outputs, and set properties for inputs and outputs</span></span>  
  
 <span data-ttu-id="e5c69-113">表示されるプロパティはコンポーネントによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e5c69-113">The properties displayed vary by component.</span></span> <span data-ttu-id="e5c69-114">**[詳細エディター]** に表示される可能性のあるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5c69-114">For more information on the properties that may be displayed in the **Advanced Editor**, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e5c69-115">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e5c69-115">Common Properties</span></span>](../../2014/integration-services/common-properties.md)  
  
-   [<span data-ttu-id="e5c69-116">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="e5c69-116">Transformation Custom Properties</span></span>](data-flow/transformations/transformation-custom-properties.md)  
  
-   [<span data-ttu-id="e5c69-117">パスのプロパティ</span><span class="sxs-lookup"><span data-stu-id="e5c69-117">Path Properties</span></span>](../../2014/integration-services/path-properties.md)  
  
 <span data-ttu-id="e5c69-118">編集している固有のコンポーネントの詳細については、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のオブジェクトと概念のドキュメントで「データ フロー要素」セクションのコンポーネントの説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5c69-118">For more information about the specific component that you are editing, see the description of the component in the Data Flow Elements section of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Objects and Concepts documentation:</span></span>  
  
-   [<span data-ttu-id="e5c69-119">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="e5c69-119">Integration Services Transformations</span></span>](data-flow/transformations/integration-services-transformations.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5c69-120">参照</span><span class="sxs-lookup"><span data-stu-id="e5c69-120">See Also</span></span>  
 [<span data-ttu-id="e5c69-121">Integration Services のエラーとメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="e5c69-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
