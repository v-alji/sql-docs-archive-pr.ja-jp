---
title: データ フロー コンポーネントのプロパティを設定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], properties
ms.assetid: 73000ef6-52a2-4dec-8320-0e79acf0c2c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1fd045ba076eed2d65d801015b881a477976f5d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644079"
---
# <a name="set-the-properties-of-a-data-flow-component"></a><span data-ttu-id="6d2d4-102">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="6d2d4-102">Set the Properties of a Data Flow Component</span></span>
  <span data-ttu-id="6d2d4-103">変換元、変換先、変換などを含むデータ フロー コンポーネントのプロパティを設定するには、次の機能のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-103">To set the properties of data flow components, which include sources, destinations, and transformations, use one of the following features:</span></span>  
  
-   <span data-ttu-id="6d2d4-104">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] が提供するコンポーネント エディター。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-104">The component editors that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="6d2d4-105">これらのエディターには、各データ フロー コンポーネントのカスタム プロパティのみ含まれます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-105">These editors include only the custom properties of each data flow component.</span></span>  
  
-   <span data-ttu-id="6d2d4-106">**[プロパティ]** ウィンドウでは、各要素のコンポーネントレベルのカスタム プロパティ、およびすべてのデータ フロー要素との共通プロパティの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-106">The **Properties** window lists the component-level custom properties of each element, as well as the properties common to all data flow elements.</span></span>  
  
-   <span data-ttu-id="6d2d4-107">**[詳細エディター]** ダイアログ ボックスでは、各コンポーネントのカスタム プロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-107">The **Advanced Editor** dialog box provides access to custom properties for each component.</span></span> <span data-ttu-id="6d2d4-108">また、 **[詳細エディター]** ダイアログ ボックスを使用すると、すべてのデータ フロー コンポーネントの共通プロパティである、入力、出力、エラー出力、列、および外部列のプロパティにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-108">The **Advanced Editor** dialog box also provides access to the properties common to all data flow components-the properties of inputs, outputs, error outputs, columns, and external columns.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-a-component-editor"></a><span data-ttu-id="6d2d4-109">コンポーネント エディターを使用してデータ フロー コンポーネントのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6d2d4-109">To set the properties of a data flow component by using a component editor</span></span>  
  
1.  <span data-ttu-id="6d2d4-110">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="6d2d4-111">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="6d2d4-112">**[制御フロー]** タブをクリックし、プロパティを表示して変更するコンポーネントのあるデータ フローが含まれる、データ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-112">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the data flow with the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="6d2d4-113">データ フロー コンポーネントをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-113">Double-click the data flow component.</span></span>  
  
5.  <span data-ttu-id="6d2d4-114">コンポーネント エディターで、プロパティ値を表示または変更し、エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-114">In the component editor, view or modify the property values, and then close the editor.</span></span>  
  
6.  <span data-ttu-id="6d2d4-115">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-115">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-properties-window"></a><span data-ttu-id="6d2d4-116">[プロパティ] ウィンドウを使用してデータ フロー コンポーネントのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6d2d4-116">To set the properties of a data flow component by using the Properties window</span></span>  
  
1.  <span data-ttu-id="6d2d4-117">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="6d2d4-118">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="6d2d4-119">**[制御フロー]** タブをクリックし、プロパティを表示して変更するコンポーネントが含まれているデータ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-119">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component whose properties you want to view and modify.</span></span>  
  
4.  <span data-ttu-id="6d2d4-120">データ フロー コンポーネントを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-120">Right-click the data flow component, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="6d2d4-121">プロパティ値を表示または変更し、 **[プロパティ]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-121">View or modify the property values, and then close the **Properties** window.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d2d4-122">プロパティの多くは読み取り専用であり、変更できません。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-122">Many properties are read-only, and cannot be modified.</span></span>  
  
6.  <span data-ttu-id="6d2d4-123">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-123">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
### <a name="to-set-the-properties-of-a-data-flow-component-by-using-the-advanced-editor"></a><span data-ttu-id="6d2d4-124">詳細エディターを使用してデータ フロー コンポーネントのプロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="6d2d4-124">To set the properties of a data flow component by using the Advanced Editor</span></span>  
  
1.  <span data-ttu-id="6d2d4-125">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-125">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="6d2d4-126">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-126">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="6d2d4-127">**[制御フロー]** タブをクリックし、表示または変更するコンポーネントが含まれているデータ フロー タスクをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-127">Click the **Control Flow** tab, and then double-click the Data Flow task that contains the component you want to view or modify.</span></span>  
  
4.  <span data-ttu-id="6d2d4-128">データ フロー デザイナーで、データ フロー コンポーネントを右クリックし、 **[詳細エディターの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-128">In the data flow designer, right-click the data flow component, and then click **Show Advanced Editor**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="6d2d4-129">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、複数の入力をサポートするデータ フロー コンポーネントで **[詳細エディター]** を使用できません。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data flow components that support multiple inputs cannot use the **Advanced Editor**.</span></span>  
  
5.  <span data-ttu-id="6d2d4-130">**[詳細エディター]** ダイアログ ボックスで、次のいずれかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-130">In the **Advanced Editor** dialog box, do any of the following steps:</span></span>  
  
    -   <span data-ttu-id="6d2d4-131">コンポーネントで使用する接続を表示および指定するには、 **[接続マネージャー]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-131">To view and specify the connection that the component uses, click the **Connection Managers** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6d2d4-132">**[接続マネージャー]** タブは、接続マネージャーを使用してファイルやデータベースなどのデータ ソースに接続するデータ フロー コンポーネントのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-132">The **Connection Managers** tab is available only to data flow components that use connection managers to connect to data sources such as files and databases</span></span>  
  
    -   <span data-ttu-id="6d2d4-133">コンポーネント レベルのプロパティを表示および変更するには、 **[コンポーネントのプロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-133">To view and modify component-level properties, click the **Component Properties** tab.</span></span>  
  
    -   <span data-ttu-id="6d2d4-134">外部列と使用できる出力との間のマッピングを表示および変更するには、 **[列マッピング]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-134">To view and modify mappings between external columns and the available output, click the **Column Mappings** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6d2d4-135">**[列マッピング]** タブは、変換元または変換先を表示または編集するときにのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-135">The **Column Mappings** tab is available only when viewing or editing sources or destinations.</span></span>  
  
    -   <span data-ttu-id="6d2d4-136">使用できる入力列の一覧を表示して、出力列の名前を更新するには、 **[入力列]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-136">To view a list of the available input columns and to update the names of output columns, click the **Input Columns** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6d2d4-137">[入力列] タブは、変換または変換先を使用した作業でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-137">The Input Columns tab is available only when working with transformations or destinations.</span></span> <span data-ttu-id="6d2d4-138">詳しくは、「 [Integration Services の変換](transformations/integration-services-transformations.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-138">For more information, see [Integration Services Transformations](transformations/integration-services-transformations.md).</span></span>  
  
    -   <span data-ttu-id="6d2d4-139">入力、出力、およびエラー出力のプロパティや、列自体のプロパティを表示および変更するには、 **[入力プロパティと出力プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-139">To view and modify the properties of inputs, outputs, and error outputs, and the properties of the columns they contain, click the **Input and Output Properties** tab.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="6d2d4-140">変換元には入力はありません。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-140">Sources have no inputs.</span></span> <span data-ttu-id="6d2d4-141">変換先には出力はありません。ただし、オプションのエラー出力がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-141">Destinations have no outputs, except for an optional error output.</span></span>  
  
6.  <span data-ttu-id="6d2d4-142">プロパティ値を表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-142">View or modify the property values.</span></span>  
  
7.  <span data-ttu-id="6d2d4-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-143">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="6d2d4-144">更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6d2d4-144">To save the updated package, on the **File** menu, click **Save Selected Items**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2d4-145">参照</span><span class="sxs-lookup"><span data-stu-id="6d2d4-145">See Also</span></span>  
 [<span data-ttu-id="6d2d4-146">Integration Services の変換</span><span class="sxs-lookup"><span data-stu-id="6d2d4-146">Integration Services Transformations</span></span>](transformations/integration-services-transformations.md)  
  
  
