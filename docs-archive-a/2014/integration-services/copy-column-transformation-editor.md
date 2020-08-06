---
title: 列コピー変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641799"
---
# <a name="copy-column-transformation-editor"></a><span data-ttu-id="f3ee6-102">列コピー変換エディター</span><span class="sxs-lookup"><span data-stu-id="f3ee6-102">Copy Column Transformation Editor</span></span>
  <span data-ttu-id="f3ee6-103">**[列コピー変換エディター]** ダイアログ ボックスを使用すると、コピーする列を選択して、新しい出力列に名前を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-103">Use the **Copy Column Transformation Editor** dialog box to select columns to copy and to assign names for the new output columns.</span></span>  
  
 <span data-ttu-id="f3ee6-104">列コピー変換の詳細については、「 [列コピー変換](data-flow/transformations/copy-column-transformation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-104">To learn more about the Copy Column transformation, see [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f3ee6-105">すべての変換元データを変換先へ単にコピーする場合、列コピー変換を使用する必要がないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-105">When you are simply copying all of your source data to a destination, it may not be necessary to use the Copy Column transformation.</span></span> <span data-ttu-id="f3ee6-106">データ変換が不要な場合、状況によっては変換元を変換先に直接接続できます。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-106">In some scenarios, you can connect a source directly to a destination, when no data transformation is required.</span></span> <span data-ttu-id="f3ee6-107">このような場合は、SQL Server インポートおよびエクスポート ウィザードを使用してパッケージを作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-107">In these circumstances it is often preferable to use the SQL Server Import and Export Wizard to create your package for you.</span></span> <span data-ttu-id="f3ee6-108">パッケージでは、必要に応じて、後から機能強化や再構成が可能です。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-108">Later you can enhance and reconfigure the package as needed.</span></span> <span data-ttu-id="f3ee6-109">詳細については、「 [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-109">For more information, see [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="f3ee6-110">Options</span><span class="sxs-lookup"><span data-stu-id="f3ee6-110">Options</span></span>  
 <span data-ttu-id="f3ee6-111">**使用できる入力列**</span><span class="sxs-lookup"><span data-stu-id="f3ee6-111">**Available Input Columns**</span></span>  
 <span data-ttu-id="f3ee6-112">チェック ボックスを使用して、コピーする列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-112">Select columns to copy by using the check boxes.</span></span> <span data-ttu-id="f3ee6-113">選択した列が入力列として下のテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-113">Your selections add input columns to the table below.</span></span>  
  
 <span data-ttu-id="f3ee6-114">**入力列**</span><span class="sxs-lookup"><span data-stu-id="f3ee6-114">**Input Column**</span></span>  
 <span data-ttu-id="f3ee6-115">使用できる入力列の一覧からコピーする列を選択します。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-115">Select columns to copy from the list of available input columns.</span></span> <span data-ttu-id="f3ee6-116">選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-116">Your selections are reflected in the check box selections in the **Available Input Columns** table.</span></span>  
  
 <span data-ttu-id="f3ee6-117">**[出力の別名]**</span><span class="sxs-lookup"><span data-stu-id="f3ee6-117">**Output Alias**</span></span>  
 <span data-ttu-id="f3ee6-118">新しい出力列の別名をそれぞれ入力します。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-118">Type an alias for each new output column.</span></span> <span data-ttu-id="f3ee6-119">既定では、入力列の名前の後に「 **のコピー**」と付きます。一意のわかりやすい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="f3ee6-119">The default is **Copy of**, followed by the name of the input column; however, you can choose any unique, descriptive name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ee6-120">参照</span><span class="sxs-lookup"><span data-stu-id="f3ee6-120">See Also</span></span>  
 [<span data-ttu-id="f3ee6-121">Integration Services のエラーおよびメッセージのリファレンス</span><span class="sxs-lookup"><span data-stu-id="f3ee6-121">Integration Services Error and Message Reference</span></span>](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
