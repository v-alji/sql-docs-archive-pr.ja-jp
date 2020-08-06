---
title: '[フラットファイルソースエディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.flatfilesourceadapter.connection.f1
helpviewer_keywords:
- Flat File Source Editor
ms.assetid: 2efd6baa-ed75-4f3f-b667-514024cebdb8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 03c1693c001dad2c8e90211b065eda208c42a07b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632601"
---
# <a name="flat-file-source-editor-connection-manager-page"></a><span data-ttu-id="25342-102">[フラット ファイル ソース エディター]\ ([接続マネージャー] ページ)</span><span class="sxs-lookup"><span data-stu-id="25342-102">Flat File Source Editor (Connection Manager Page)</span></span>
  <span data-ttu-id="25342-103">**[フラット ファイル ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、フラット ファイル ソースが使用する接続マネージャーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="25342-103">Use the **Connection Manager** page of the **Flat File Source Editor** dialog box to select the connection manager that the Flat File source will use.</span></span> <span data-ttu-id="25342-104">フラット ファイル ソースは、区切り形式、固定幅形式、または区切りと固定幅が混在した形式のテキスト ファイルからデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="25342-104">The Flat File source reads data from a text file, which can be in a delimited, fixed width, or mixed format.</span></span>  
  
 <span data-ttu-id="25342-105">フラット ファイル ソースは、次のいずれかの種類の接続マネージャーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="25342-105">A Flat File source can use one of the following types of connection managers:</span></span>  
  
-   <span data-ttu-id="25342-106">ソースが単一のフラット ファイルの場合は、フラット ファイル接続マネージャー。</span><span class="sxs-lookup"><span data-stu-id="25342-106">A Flat File connection manager if the source is a single flat file.</span></span> <span data-ttu-id="25342-107">詳しくは、「 [フラット ファイル接続マネージャー](connection-manager/file-connection-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="25342-107">For more information, see [Flat File Connection Manager](connection-manager/file-connection-manager.md).</span></span>  
  
-   <span data-ttu-id="25342-108">ソースが複数フラット ファイルで、データ フロー タスクが For ループ コンテナーなどのループ コンテナーの内部にある場合は、複数フラット ファイル接続マネージャー。</span><span class="sxs-lookup"><span data-stu-id="25342-108">A Multiple Flat Files connection manager if the source is multiple flat files and the Data Flow task is inside a loop container, such as the For Loop container.</span></span> <span data-ttu-id="25342-109">コンテナーの各ループで、フラット ファイル ソースは、複数フラット ファイル接続マネージャーが提供する次のファイル名からデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="25342-109">On each loop of the container, the Flat File source loads data from the next file name that the Multiple Flat Files connection manager provides.</span></span> <span data-ttu-id="25342-110">詳細については、「 [複数フラット ファイル接続マネージャー](connection-manager/multiple-flat-files-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25342-110">For more information, see [Multiple Flat Files Connection Manager](connection-manager/multiple-flat-files-connection-manager.md).</span></span>  
  
 <span data-ttu-id="25342-111">フラット ファイル ソースの詳細については、「 [Flat File Source](data-flow/flat-file-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25342-111">To learn more about the Flat File source, see [Flat File Source](data-flow/flat-file-source.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="25342-112">Options</span><span class="sxs-lookup"><span data-stu-id="25342-112">Options</span></span>  
 <span data-ttu-id="25342-113">**フラットファイル接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="25342-113">**Flat file connection manager**</span></span>  
 <span data-ttu-id="25342-114">既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="25342-114">Select an existing connection manager from the list, or create a new connection manager by clicking **New**.</span></span>  
  
 <span data-ttu-id="25342-115">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="25342-115">**New**</span></span>  
 <span data-ttu-id="25342-116">新しい接続マネージャーを作成するには、 **[フラット ファイル接続マネージャー エディター]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="25342-116">Create a new connection manager by using the **Flat File Connection Manager Editor** dialog box.</span></span>  
  
 <span data-ttu-id="25342-117">**[データ ソースの NULL 値をデータ フローで NULL 値として保持する]**</span><span class="sxs-lookup"><span data-stu-id="25342-117">**Retain null values from the source as null values in the data flow**</span></span>  
 <span data-ttu-id="25342-118">データが抽出されたときに NULL 値を保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="25342-118">Specify whether to keep null values when data is extracted.</span></span> <span data-ttu-id="25342-119">このプロパティの既定値は **false**です。</span><span class="sxs-lookup"><span data-stu-id="25342-119">The default value of this property is **false**.</span></span> <span data-ttu-id="25342-120">この値が `alse` である場合、フラット ファイル変換元は変換元データの NULL 値を各列の適切な既定値で置き換えます。たとえば、文字列型の列の場合は空の文字列、数値型の列の場合は 0 です。</span><span class="sxs-lookup"><span data-stu-id="25342-120">When this value is f`alse`, the Flat File source replaces null values from the source data with appropriate default values for each column, such as empty strings for string columns and zero for numeric columns.</span></span>  
  
 <span data-ttu-id="25342-121">**プレビュー**</span><span class="sxs-lookup"><span data-stu-id="25342-121">**Preview**</span></span>  
 <span data-ttu-id="25342-122">**[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。</span><span class="sxs-lookup"><span data-stu-id="25342-122">Preview results by using the **Data View** dialog box.</span></span> <span data-ttu-id="25342-123">プレビューでは、最大で 200 行を表示できます。</span><span class="sxs-lookup"><span data-stu-id="25342-123">Preview can display up to 200 rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25342-124">参照</span><span class="sxs-lookup"><span data-stu-id="25342-124">See Also</span></span>  
 <span data-ttu-id="25342-125">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="25342-125">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="25342-126">[[フラットファイルソースエディター] &#40;[列] ページ&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span><span class="sxs-lookup"><span data-stu-id="25342-126">[Flat File Source Editor &#40;Columns Page&#41;](../../2014/integration-services/flat-file-source-editor-columns-page.md) </span></span>  
 <span data-ttu-id="25342-127">[フラットファイルソースエディター &#40;エラー出力ページ&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span><span class="sxs-lookup"><span data-stu-id="25342-127">[Flat File Source Editor &#40;Error Output Page&#41;](../../2014/integration-services/flat-file-source-editor-error-output-page.md) </span></span>  
 [<span data-ttu-id="25342-128">フラット ファイル接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="25342-128">Flat File Connection Manager</span></span>](connection-manager/file-connection-manager.md)  
  
  
