---
title: XML ソースを使用してデータを抽出する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], XML
- XML source [Integration Services]
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57758353c476badfba4cb12a1ef6b5101f16735d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742429"
---
# <a name="extract-data-by-using-the-xml-source"></a><span data-ttu-id="a65b0-102">XML ソースを使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="a65b0-102">Extract Data by Using the XML Source</span></span>
  <span data-ttu-id="a65b0-103">XML ソースを追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクがあらかじめ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a65b0-103">To add and configure an XML source, the package must already include at least one Data Flow task.</span></span>  
  
### <a name="to-extract-data-using-an-xml-source"></a><span data-ttu-id="a65b0-104">XML ソースを使用してデータを抽出するには</span><span class="sxs-lookup"><span data-stu-id="a65b0-104">To extract data using an XML source</span></span>  
  
1.  <span data-ttu-id="a65b0-105">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a65b0-105">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a65b0-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a65b0-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a65b0-107">**[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、XML ソースをデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a65b0-107">Click the **Data Flow** tab, and then, from the **Toolbox**, drag the XML source to the design surface.</span></span>  
  
4.  <span data-ttu-id="a65b0-108">XML ソースをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65b0-108">Double-click the XML source.</span></span>  
  
5.  <span data-ttu-id="a65b0-109">**[XML ソース エディター]** の **[接続マネージャー]** ページで、データ アクセス モードを次のうちから選択します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-109">In the **XML Source Editor**, on the **Connection Manager** page, select a data access mode:</span></span>  
  
    -   <span data-ttu-id="a65b0-110">**[XML ファイルの場所]** アクセス モードでは、 **[参照]** をクリックし、XML ファイルが含まれるフォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-110">For the **XML file location** access mode, click **Browse** and locate the folder that contains the XML file.</span></span>  
  
    -   <span data-ttu-id="a65b0-111">**[変数からの XML ファイル]** アクセス モードでは、XML ファイルのパスが含まれるユーザー定義変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-111">For the **XML file from variable** access mode, select the user-defined variable that contains the path of the XML file.</span></span>  
  
    -   <span data-ttu-id="a65b0-112">**[変数からの XML データ]** アクセス モードでは、XML データが含まれるユーザー定義変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-112">For the **XML data from variable** access mode, select the user-defined variable that contains the XML data.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a65b0-113">変数は、XML ソースが含まれるデータ フロー タスクのスコープ内、またはパッケージのスコープ内で定義する必要があります。また、変数は文字列データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a65b0-113">The variables must be defined in the scope of the Data Flow task that contains the XML source, or in the scope of the package; additionally, the variable must have a string data type.</span></span>  
  
6.  <span data-ttu-id="a65b0-114">必要に応じて、 **[インライン スキーマを使用する]** を選択し、スキーマ情報が含まれる XML ドキュメントを指定します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-114">Optionally, select **Use inline schema** to indicate that the XML document includes schema information.</span></span>  
  
7.  <span data-ttu-id="a65b0-115">XML ファイルに対して、外部の XML Schema Definition Language (XSD) スキーマを指定するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a65b0-115">To specify an external XML Schema definition language (XSD) schema for the XML file, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a65b0-116">**[参照]** をクリックして既存の XSD ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-116">Click **Browse** to locate an existing XSD file.</span></span>  
  
    -   <span data-ttu-id="a65b0-117">**[XSD の生成]** をクリックして、XML ファイルから XSD を作成します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-117">Click **Generate XSD** to create an XSD from the XML file.</span></span>  
  
8.  <span data-ttu-id="a65b0-118">出力列の名前を更新するには、 **[列]** をクリックし、 **[出力列]** 一覧の値を編集します。</span><span class="sxs-lookup"><span data-stu-id="a65b0-118">To update the names of output columns, click **Columns** and edit the values in the **Output Column** list.</span></span>  
  
9. <span data-ttu-id="a65b0-119">エラー出力を構成するには、 **[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65b0-119">To configure the error output, click **Error Output**.</span></span> <span data-ttu-id="a65b0-120">詳細については、「 [データ フロー コンポーネントでエラー出力を構成する](../configure-an-error-output-in-a-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a65b0-120">For more information, see [Configure an Error Output in a Data Flow Component](../configure-an-error-output-in-a-data-flow-component.md).</span></span>  
  
10. <span data-ttu-id="a65b0-121">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65b0-121">Click **OK**.</span></span>  
  
11. <span data-ttu-id="a65b0-122">更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a65b0-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65b0-123">参照</span><span class="sxs-lookup"><span data-stu-id="a65b0-123">See Also</span></span>  
 <span data-ttu-id="a65b0-124">[XML ソース](xml-source.md) </span><span class="sxs-lookup"><span data-stu-id="a65b0-124">[XML Source](xml-source.md) </span></span>  
 <span data-ttu-id="a65b0-125">[Integration Services の変換](transformations/integration-services-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="a65b0-125">[Integration Services Transformations](transformations/integration-services-transformations.md) </span></span>  
 <span data-ttu-id="a65b0-126">[Integration Services のパス](integration-services-paths.md) </span><span class="sxs-lookup"><span data-stu-id="a65b0-126">[Integration Services Paths](integration-services-paths.md) </span></span>  
 [<span data-ttu-id="a65b0-127">データ フロー タスク</span><span class="sxs-lookup"><span data-stu-id="a65b0-127">Data Flow Task</span></span>](../control-flow/data-flow-task.md)  
  
  
