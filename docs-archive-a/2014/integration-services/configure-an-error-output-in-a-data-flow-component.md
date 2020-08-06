---
title: データフローコンポーネントでエラー出力を構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- errors [Integration Services], data flow components
- components [Integration Services], data flow
- error outputs [Integration Services]
ms.assetid: 53d7eeea-927d-4b45-8ea9-084e65ad5390
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebd44383e27daa465576bb056a67f6dacad87b0a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741197"
---
# <a name="configure-an-error-output-in-a-data-flow-component"></a><span data-ttu-id="a748a-102">データ フロー コンポーネントでエラー出力を構成する</span><span class="sxs-lookup"><span data-stu-id="a748a-102">Configure an Error Output in a Data Flow Component</span></span>
  <span data-ttu-id="a748a-103">多くのデータ フロー コンポーネントがエラー出力をサポートしており、 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでエラー出力を構成する方法は、コンポーネントに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="a748a-103">Many data flow components support error outputs, and depending on the component, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides different ways to configure an error output.</span></span> <span data-ttu-id="a748a-104">エラー出力の構成以外に、エラー出力の列を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a748a-104">In addition to configuring an error output, you can also configure the columns of an error output.</span></span> <span data-ttu-id="a748a-105">これには、コンポーネントによって追加される **[ErrorCode]** 列や **[ErrorColumn]** 列の構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a748a-105">This includes configuring the **ErrorCode** and **ErrorColumn** columns that are added by the component.</span></span>  
  
## <a name="configuring-an-error-output"></a><span data-ttu-id="a748a-106">エラー出力の構成</span><span class="sxs-lookup"><span data-stu-id="a748a-106">Configuring an Error Output</span></span>  
 <span data-ttu-id="a748a-107">エラー出力を構成する場合、2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="a748a-107">To configure an error output, you have two options:</span></span>  
  
-   <span data-ttu-id="a748a-108">**[エラー出力の構成]** ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a748a-108">Use the **Configure Error Output** dialog box.</span></span> <span data-ttu-id="a748a-109">このダイアログ ボックスを使用すると、エラー出力をサポートするデータ フロー コンポーネントでエラー出力を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a748a-109">You can use this dialog box to configure an error output on any data flow component that supports an error output.</span></span>  
  
-   <span data-ttu-id="a748a-110">コンポーネントのエディター ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a748a-110">Use the editor dialog box for the component.</span></span> <span data-ttu-id="a748a-111">いくつかのコンポーネントでは、エディター ダイアログ ボックスから直接エラー出力を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a748a-111">Some components let you configure error outputs directly from their editor dialog box.</span></span> <span data-ttu-id="a748a-112">ただし、ADO NET ソース、列インポート変換、OLE DB コマンド変換、または [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact 変換先のエディター ダイアログ ボックスからはエラー出力を構成できません。</span><span class="sxs-lookup"><span data-stu-id="a748a-112">However, you cannot configure error outputs from the editor dialog box for the ADO NET source, the Import Column transformation, the OLE DB Command transformation, or the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact destination.</span></span>  
  
 <span data-ttu-id="a748a-113">次の手順では、これらのダイアログ ボックスを使用してエラー出力を構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a748a-113">The following procedures describe how to use these dialog boxes to configure error outputs.</span></span>  
  
#### <a name="to-configure-an-error-output-using-the-configure-error-output-dialog-box"></a><span data-ttu-id="a748a-114">[エラー出力の構成] ダイアログ ボックスを使用してエラー出力を構成するには</span><span class="sxs-lookup"><span data-stu-id="a748a-114">To configure an error output using the Configure Error Output dialog box</span></span>  
  
1.  <span data-ttu-id="a748a-115">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-115">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a748a-116">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-116">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a748a-117">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-117">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a748a-118">赤い矢印で表示されているエラー出力を、エラー元のコンポーネントからデータ フローの別のコンポーネントにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="a748a-118">Drag the error output, represented by the red arrow, from the component that is the source of the errors to another component in the data flow.</span></span>  
  
5.  <span data-ttu-id="a748a-119">**[エラー出力の構成]** ダイアログ ボックスで、コンポーネントの入力の各列について、 **[エラー]** 列および **[切り捨て]** 列のアクションを選択します。</span><span class="sxs-lookup"><span data-stu-id="a748a-119">In the **Configure Error Output** dialog box, select an action in the **Error** and **Truncation** columns for each column in the component input.</span></span>  
  
6.  <span data-ttu-id="a748a-120">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-120">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
#### <a name="to-add-an-error-output-using-the-editor-dialog-box-for-the-component"></a><span data-ttu-id="a748a-121">コンポーネントのエディター ダイアログ ボックスを使用してエラー出力を追加するには</span><span class="sxs-lookup"><span data-stu-id="a748a-121">To add an error output using the editor dialog box for the component</span></span>  
  
1.  <span data-ttu-id="a748a-122">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a748a-123">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a748a-124">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-124">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a748a-125">エラー出力を構成するデータ フロー コンポーネントをダブルクリックし、コンポーネントに応じて、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a748a-125">Double-click the data flow components in which you want to configure an error output and, depending on the component, do one of the following steps:</span></span>  
  
    -   <span data-ttu-id="a748a-126">**[エラー出力の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-126">Click **Configure Error Output**.</span></span>  
  
    -   <span data-ttu-id="a748a-127">**[エラー出力]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-127">Click **Error Output**.</span></span>  
  
5.  <span data-ttu-id="a748a-128">各列の **[エラー]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a748a-128">Set the **Error** option for each column.</span></span>  
  
6.  <span data-ttu-id="a748a-129">各列の **[切り捨て]** オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a748a-129">Set the **Truncation** option for each column.</span></span>  
  
7.  <span data-ttu-id="a748a-130">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-130">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="a748a-131">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-131">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="configuring-error-output-columns"></a><span data-ttu-id="a748a-132">エラー出力列の構成</span><span class="sxs-lookup"><span data-stu-id="a748a-132">Configuring Error Output Columns</span></span>  
 <span data-ttu-id="a748a-133">エラー出力列を構成するには、 **[詳細エディター]** ダイアログ ボックスの **[入力プロパティと出力プロパティ]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="a748a-133">To configure the error output columns, you have to use the **Input and Output Properties** tab of the **Advanced Editor** dialog box.</span></span>  
  
#### <a name="to-configure-error-output-columns"></a><span data-ttu-id="a748a-134">エラー出力列を構成するには</span><span class="sxs-lookup"><span data-stu-id="a748a-134">To configure error output columns</span></span>  
  
1.  <span data-ttu-id="a748a-135">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-135">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="a748a-136">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="a748a-136">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="a748a-137">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[データ フロー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-137">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Data Flow** tab.</span></span>  
  
4.  <span data-ttu-id="a748a-138">構成するエラー出力列が含まれているコンポーネントを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-138">Right-click the component whose error output columns you want to configure and click **Show Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="a748a-139">**[入力プロパティと出力プロパティ]** タブをクリックして、 **[\<component name> のエラー出力]** を展開してから **[出力列]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="a748a-139">Click the **Input and Output Properties** tab and expand **\<component name> Error Output** and then expand **Output Columns**.</span></span>  
  
6.  <span data-ttu-id="a748a-140">列をクリックして、プロパティを更新します。</span><span class="sxs-lookup"><span data-stu-id="a748a-140">Click a column and update its properties.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a748a-141">列の一覧には、コンポーネントの入力列、前のエラー出力で追加された **[ErrorCode]** 列と **[ErrorColumn]** 列、このコンポーネントによって追加された **[ErrorCode]** 列と **[ErrorColumn]** 列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a748a-141">The list of columns includes the columns in the component input, the **ErrorCode** and **ErrorColumn** columns added by previous error outputs, and the **ErrorCode** and **ErrorColumn** columns added by this component.</span></span>  
  
7.  <span data-ttu-id="a748a-142">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-142">Click **OK.**</span></span>  
  
8.  <span data-ttu-id="a748a-143">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a748a-143">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a748a-144">参照</span><span class="sxs-lookup"><span data-stu-id="a748a-144">See Also</span></span>  
 [<span data-ttu-id="a748a-145">データのエラー処理</span><span class="sxs-lookup"><span data-stu-id="a748a-145">Error Handling in Data</span></span>](data-flow/error-handling-in-data.md)  
  
  
