---
title: 列インポート変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.importcolumntrans.f1
helpviewer_keywords:
- Import Column transformation [Integration Services]
- columns [Integration Services], importing
- importing data, SSIS packages
- inserting data
ms.assetid: ac3b74c1-ef54-4297-8062-1734324fffcc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f4330438614cce7892e74dc9a1dcbb6680b72972
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644063"
---
# <a name="import-column-transformation"></a><span data-ttu-id="8a3ad-102">列インポート変換</span><span class="sxs-lookup"><span data-stu-id="8a3ad-102">Import Column Transformation</span></span>
  <span data-ttu-id="8a3ad-103">列インポート変換は、ファイルのデータを読み取り、そのデータをデータ フローの列に追加します。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-103">The Import Column transformation reads data from files and adds the data to columns in a data flow.</span></span> <span data-ttu-id="8a3ad-104">この変換を使用すると、パッケージは、別々のファイルに格納されているテキストや画像を 1 つのデータ フローに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-104">Using this transformation, a package can add text and images stored in separate files to a data flow.</span></span> <span data-ttu-id="8a3ad-105">たとえば、製品情報を保存するテーブルにデータを読み込むデータ フローに列インポート変換を含めると、各製品に対する顧客評価をファイルからインポートし、データ フローに追加できます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-105">For example, a data flow that loads data into a table that stores product information can include the Import Column transformation to import customer reviews of each product from files and add the reviews to the data flow.</span></span>  
  
 <span data-ttu-id="8a3ad-106">列インポート変換は、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-106">You can configure the Import Column transformation in the following ways:</span></span>  
  
-   <span data-ttu-id="8a3ad-107">データを追加する列を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-107">Specify the columns to which the transformation adds data.</span></span>  
  
-   <span data-ttu-id="8a3ad-108">バイト順マーク (BOM) が必要かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-108">Specify whether the transformation expects a byte-order mark (BOM).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8a3ad-109">BOM が必要になるのは、データが DT_NTEXT データ型の場合だけです。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-109">A BOM is only expected if the data has the DT_NTEXT data type.</span></span>  
  
 <span data-ttu-id="8a3ad-110">変換入力の列には、データを保持するファイル名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-110">A column in the transformation input contains the names of files that hold the data.</span></span> <span data-ttu-id="8a3ad-111">データセットの各行には、異なるファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-111">Each row in the dataset can specify a different file.</span></span> <span data-ttu-id="8a3ad-112">列インポート変換が行を処理すると、ファイル名を読み取り、ファイル システム内の対応するファイルを開き、ファイルの内容を出力列に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-112">When the Import Column transformation processes a row, it reads the file name, opens the corresponding file in the file system, and loads the file content into an output column.</span></span> <span data-ttu-id="8a3ad-113">出力列のデータ型は、DT_TEXT、DT_NTEXT、または DT_IMAGE 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-113">The data type of the output column must be DT_TEXT, DT_NTEXT, or DT_IMAGE.</span></span> <span data-ttu-id="8a3ad-114">詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-114">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="8a3ad-115">この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-115">This transformation has one input, one output, and one error output.</span></span>  
  
## <a name="configuration-of-the-import-column-transformation"></a><span data-ttu-id="8a3ad-116">列インポート変換の構成</span><span class="sxs-lookup"><span data-stu-id="8a3ad-116">Configuration of the Import Column Transformation</span></span>  
 <span data-ttu-id="8a3ad-117">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-117">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="8a3ad-118">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-118">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="8a3ad-119">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-119">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="8a3ad-120">Common Properties</span><span class="sxs-lookup"><span data-stu-id="8a3ad-120">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="8a3ad-121">変換のカスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="8a3ad-121">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="8a3ad-122">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8a3ad-122">Related Tasks</span></span>  
 <span data-ttu-id="8a3ad-123">このコンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a3ad-123">For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../set-the-properties-of-a-data-flow-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3ad-124">参照</span><span class="sxs-lookup"><span data-stu-id="8a3ad-124">See Also</span></span>  
 <span data-ttu-id="8a3ad-125">[列エクスポート変換](export-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="8a3ad-125">[Export Column Transformation](export-column-transformation.md) </span></span>  
 <span data-ttu-id="8a3ad-126">[データ フロー](../data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="8a3ad-126">[Data Flow](../data-flow.md) </span></span>  
 [<span data-ttu-id="8a3ad-127">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="8a3ad-127">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  
