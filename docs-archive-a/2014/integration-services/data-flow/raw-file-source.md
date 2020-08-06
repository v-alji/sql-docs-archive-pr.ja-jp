---
title: RAW ファイル ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfilesource.f1
helpviewer_keywords:
- sources [Integration Services], Raw File
- raw data [Integration Services]
- Raw File source
ms.assetid: 5b4daea5-7f76-4674-aa77-0a79f9f97f7d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4cbc5800c4fb2b90b74e66b6ff161118b2b550f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633919"
---
# <a name="raw-file-source"></a><span data-ttu-id="ebfd1-102">RAW ファイル ソース (Raw File source)</span><span class="sxs-lookup"><span data-stu-id="ebfd1-102">Raw File Source</span></span>
  <span data-ttu-id="ebfd1-103">RAW ファイル ソースは、ファイルから生データを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-103">The Raw File source reads raw data from a file.</span></span> <span data-ttu-id="ebfd1-104">データはソース ファイル固有の方法で表示されるため、変換の必要がなく、ほとんどの場合は解析の必要もありません。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-104">Because the representation of the data is native to the source, the data requires no translation and almost no parsing.</span></span> <span data-ttu-id="ebfd1-105">したがって、RAW ファイル ソースは、フラット ファイルや OLE DB などの他のソースよりも、高速にデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-105">This means that the Raw File source can read data more quickly than other sources such as the Flat File and the OLE DB sources.</span></span>  
  
 <span data-ttu-id="ebfd1-106">RAW ファイル ソースは、以前 RAW ファイルの変換先に記述された生データを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-106">The Raw File source is used to retrieve raw data that was previously written by the Raw File destination.</span></span> <span data-ttu-id="ebfd1-107">また、RAW ファイル ソースの参照先を、列のみを含む空の RAW ファイル (メタデータのみのファイル) にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-107">You can also point the Raw File source to an empty raw file that contains only the columns (metadata-only file).</span></span> <span data-ttu-id="ebfd1-108">パッケージを実行せずにメタデータのみのファイルを生成するには、RAW ファイル変換先を使用します。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-108">You use the Raw File destination to generate the metadata-only file without having to run the package.</span></span> <span data-ttu-id="ebfd1-109">詳細については、「 [RAW ファイル変換先](raw-file-destination.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-109">For more information, see [Raw File Destination](raw-file-destination.md).</span></span>  
  
 <span data-ttu-id="ebfd1-110">RAW ファイルの形式には、並べ替えの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-110">The raw file format contains sort information.</span></span> <span data-ttu-id="ebfd1-111">RAW ファイル変換先には、文字列の列の比較フラグを含む並べ替えの情報がすべて保存されます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-111">The Raw File Destination saves all the sort information including the comparison flags for string columns.</span></span> <span data-ttu-id="ebfd1-112">RAW ファイル ソースは、並べ替えの情報を読み取って受け入れます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-112">The Raw File source reads and honors the sort information.</span></span> <span data-ttu-id="ebfd1-113">詳細エディターを使用して、ファイル内の並べ替えのフラグを無視するように RAW ファイル ソースを構成するためのオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-113">You do have the option of configuring the Raw File Source to ignore the sort flags in the file, using the Advanced Editor.</span></span> <span data-ttu-id="ebfd1-114">比較フラグの詳細については、「 [文字列データの比較](comparing-string-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-114">For more information about comparison flags, see [Comparing String Data](comparing-string-data.md).</span></span>  
  
 <span data-ttu-id="ebfd1-115">RAW ファイルを構成するには、RAW ファイル ソースが読み取るファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-115">You configure the Raw File by specifying the name of the name of the file that the Raw File source reads.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ebfd1-116">このソースでは、接続マネージャーは使用されません。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-116">This source does not use a connection manager.</span></span>  
  
 <span data-ttu-id="ebfd1-117">このソースは、1 つの出力をとります。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-117">This source has one output.</span></span> <span data-ttu-id="ebfd1-118">エラー出力はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-118">It does not support an error output.</span></span>  
  
## <a name="configuration-of-the-raw-file-source"></a><span data-ttu-id="ebfd1-119">RAW ファイル ソースの構成</span><span class="sxs-lookup"><span data-stu-id="ebfd1-119">Configuration of the Raw File Source</span></span>  
 <span data-ttu-id="ebfd1-120">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-120">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="ebfd1-121">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-121">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="ebfd1-122">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-122">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="ebfd1-123">Common Properties</span><span class="sxs-lookup"><span data-stu-id="ebfd1-123">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="ebfd1-124">RAW ファイルのカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="ebfd1-124">Raw File Custom Properties</span></span>](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="ebfd1-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ebfd1-125">Related Tasks</span></span>  
 <span data-ttu-id="ebfd1-126">コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebfd1-126">For information about how to set the properties of the component, see [Set the Properties of a Data Flow Component](set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ebfd1-127">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ebfd1-127">Related Content</span></span>  
  
-   <span data-ttu-id="ebfd1-128">sqlservercentral.com のブログ「 [RAW ファイルは最高](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131)」</span><span class="sxs-lookup"><span data-stu-id="ebfd1-128">Blog entry, [Raw Files Are Awesome](https://www.sqlservercentral.com/blogs/31-days-of-ssis-%e2%80%93-raw-files-are-awesome-131), on sqlservercentral.com</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfd1-129">参照</span><span class="sxs-lookup"><span data-stu-id="ebfd1-129">See Also</span></span>  
 <span data-ttu-id="ebfd1-130">[Raw ファイル変換先](raw-file-destination.md) </span><span class="sxs-lookup"><span data-stu-id="ebfd1-130">[Raw File Destination](raw-file-destination.md) </span></span>  
 [<span data-ttu-id="ebfd1-131">データ フロー</span><span class="sxs-lookup"><span data-stu-id="ebfd1-131">Data Flow</span></span>](data-flow.md)  
  
  
