---
title: Foreach ループコンテナーを構成する |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Foreach Loop containers
- containers [Integration Services], Foreach Loop
ms.assetid: 519c6f96-5e1f-47d2-b96a-d49946948c25
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 85fb399f51e22e091fac9b1d8d332b9a12e7d77e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632626"
---
# <a name="configure-a-foreach-loop-container"></a><span data-ttu-id="85a69-102">Foreach ループ コンテナーを構成する</span><span class="sxs-lookup"><span data-stu-id="85a69-102">Configure a Foreach Loop Container</span></span>
  <span data-ttu-id="85a69-103">この手順では、列挙子レベルおよびコンテナー レベルでのプロパティ式など、Foreach ループ コンテナーを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85a69-103">This procedure describes how to configure a Foreach Loop container, including property expressions at the enumerator and container levels.</span></span>  
  
### <a name="to-configure-the-foreach-loop-container"></a><span data-ttu-id="85a69-104">Foreach ループ コンテナーを構成するには</span><span class="sxs-lookup"><span data-stu-id="85a69-104">To configure the Foreach Loop container</span></span>  
  
1.  <span data-ttu-id="85a69-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="85a69-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="85a69-106">**[制御フロー]** タブをクリックし、Foreach ループをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-106">Click the **Control Flow** tab and double-click the Foreach Loop.</span></span>  
  
3.  <span data-ttu-id="85a69-107">**[Foreach ループ エディター]** ダイアログ ボックスで **[全般]** をクリックし、必要に応じて Foreach ループの名前と説明を変更します。</span><span class="sxs-lookup"><span data-stu-id="85a69-107">In the **Foreach Loop Editor** dialog box, click **General** and, optionally, modify the name and description of the Foreach Loop.</span></span>  
  
4.  <span data-ttu-id="85a69-108">**[コレクション]** をクリックし、 **[Enumerator]** 一覧から列挙子の型を選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-108">Click **Collection** and select an enumerator type from the **Enumerator** list.</span></span>  
  
5.  <span data-ttu-id="85a69-109">列挙子を指定し、列挙子のオプションを次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="85a69-109">Specify an enumerator and set enumerator options as follows:</span></span>  
  
    -   <span data-ttu-id="85a69-110">Foreach File 列挙子を使用するには、列挙するファイルが含まれるフォルダーを指定し、ファイル名と種類に対するフィルターを指定します。次に、完全修飾ファイル名を返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="85a69-110">To usethe Foreach File enumerator, provide the folder that contains the files to enumerate, specify a filter for the file name and type, and specify whether the fully qualified file name should be returned.</span></span> <span data-ttu-id="85a69-111">また、サブフォルダーを再帰的に使用して、より多くのファイルを列挙するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="85a69-111">Also, indicate whether to recurse through subfolders for more files.</span></span>  
  
    -   <span data-ttu-id="85a69-112">Foreach Item 列挙子を使用するには、 **[列]** をクリックし、 **[For Each Item 列]** ダイアログ ボックスで **[追加]** をクリックして列を追加します。</span><span class="sxs-lookup"><span data-stu-id="85a69-112">To use the Foreach Item enumerator, click **Columns**, and, in the **For Each Item Columns** dialog box, click **Add** to add columns.</span></span> <span data-ttu-id="85a69-113">**[データ型]** 一覧で各列のデータ型を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-113">Select a data type in the **Data Type** list for each column, and click **OK**.</span></span>  
  
         <span data-ttu-id="85a69-114">列の値を入力するか、一覧から値を選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-114">Type values in the columns or select values from lists.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="85a69-115">新しい行を追加するには、入力したセルの外側の任意の場所をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-115">To add a new row, click anywhere outside the cell in which you typed.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="85a69-116">値が列のデータ型と互換性がない場合、テキストが強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="85a69-116">If a value is not compatible with the column data type, the text is highlighted.</span></span>  
  
    -   <span data-ttu-id="85a69-117">Foreach ADO 列挙子を使用するには、 **[ADO オブジェクト ソース変数]** の一覧で既存の変数を選択するか、または **[新しい変数]** をクリックして、列挙する ADO オブジェクトの名前を保持する変数を指定します。次に、列挙モードのオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-117">To use the Foreach ADO enumerator, select an existing variable or click **New variable** in the **ADO object source variable** list to specify the variable that contains the name of the ADO object to enumerate, and select an enumeration mode option.</span></span>  
  
         <span data-ttu-id="85a69-118">新しい変数を作成する場合、 **[変数の追加]** ダイアログ ボックスで変数のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="85a69-118">If creating a new variable, set the variable properties in the **Add Variable** dialog box.</span></span>  
  
    -   <span data-ttu-id="85a69-119">Foreach ADO.NET Schema Rowset 列挙子を使用するには、 **[接続]** 一覧で既存の ADO.NET 接続を選択するか、または **[新しい接続]** をクリックします。次に、スキーマを選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-119">To use the Foreach ADO.NET Schema Rowset enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then select a schema.</span></span>  
  
         <span data-ttu-id="85a69-120">必要に応じて、 **[制限の設定]** をクリックしてスキーマの制限を選択するか、制限値が含まれる変数を選択するか、または制限値を入力します。次に、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-120">Optionally, click **Set Restrictions** and select schema restrictions, select the variable that contains the restriction value or type the restriction value, and click **OK**.</span></span>  
  
    -   <span data-ttu-id="85a69-121">Foreach From Variable 列挙子を使用するには、 **[変数]** 一覧で変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-121">To use the Foreach From Variable enumerator, select a variable in the **Variable** list.</span></span>  
  
    -   <span data-ttu-id="85a69-122">Foreach NodeList 列挙子を使用するには、[DocumentSourceType] をクリックし、リストからソースの種類を選択し、[DocumentSource] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-122">To use the Foreach NodeList enumerator, click DocumentSourceType and select the source type from the list, and then click DocumentSource.</span></span> <span data-ttu-id="85a69-123">選択した DocumentSourceType の値に応じて、一覧から変数またはファイル接続を選択するか、新しい変数またはファイル接続を作成するか、 **[ドキュメント ソース エディター]** で XML ソースを入力します。</span><span class="sxs-lookup"><span data-stu-id="85a69-123">Depending on the value selected for DocumentSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the XML source in the **Document Source Editor**.</span></span>  
  
         <span data-ttu-id="85a69-124">次に、[EnumerationType] をクリックし、一覧から列挙型を選択します。</span><span class="sxs-lookup"><span data-stu-id="85a69-124">Next, click EnumerationType and select an enumeration type from the list.</span></span> <span data-ttu-id="85a69-125">[EnumerationType] が **[Navigator]、[Node]、または [NodeText]** の場合、[OuterXPathStringSourceType] をクリックし、ソースの種類を選択し、[OuterXPathString] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-125">If EnumerationType is **Navigator, Node, or NodeText**, click OuterXPathStringSourceType and select the source type, and then click OuterXPathString.</span></span> <span data-ttu-id="85a69-126">設定した OuterXPathStringSourceType の値に応じて、一覧から変数またはファイル接続を選択するか、新しい変数またはファイル接続を作成するか、外部の XML パス言語 (XPath) 式の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="85a69-126">Depending on the value set for OuterXPathStringSourceType, select a variable or a file connection from the list, create a new variable or file connection, or type the string for the outer XML Path Language (XPath) expression.</span></span>  
  
         <span data-ttu-id="85a69-127">[EnumerationType] が **[ElementCollection]** の場合、前述のように [OuterXPathStringSourceType] と [OuterXPathString] を設定します。</span><span class="sxs-lookup"><span data-stu-id="85a69-127">If EnumerationType is **ElementCollection**,set OuterXPathStringSourceType and OuterXPathString as described above.</span></span> <span data-ttu-id="85a69-128">次に [InnerElementType] をクリックし、内部要素の 列挙型を選択し、[InnerXPathStringSourceType] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-128">Then, click InnerElementType and select an enumeration type for the inner elements, and then click InnerXPathStringSourceType.</span></span> <span data-ttu-id="85a69-129">設定した InnerXPathStringSourceType の値に応じて、変数またはファイル接続を選択するか、新しい変数またはファイル接続を作成するか、内部の XPath 式の文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="85a69-129">Depending on the value set for InnerXPathStringSourceType, select a variable or a file connection, create a new variable or file connection, or type the string for the inner XPath expression.</span></span>  
  
    -   <span data-ttu-id="85a69-130">Foreach SMO 列挙子を使用するには、 **[接続]** 一覧で既存の ADO.NET 接続を選択するか、 **[新しい接続]** をクリックします。次に、使用する文字列を入力するか、 **[参照]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-130">To use the Foreach SMO enumerator, select an existing ADO.NET connection or click **New connection** in the **Connection** list, and then either type the string to use or click **Browse**.</span></span> <span data-ttu-id="85a69-131">**[参照]** をクリックした場合は、 **[SMO 列挙の選択]** ダイアログ ボックスで、列挙するオブジェクトの種類と列挙型を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-131">If you click **Browse**, in the **Select SMO Enumeration** dialog box, select the object type to enumerate and the enumeration type, and click **OK**.</span></span>  
  
6.  <span data-ttu-id="85a69-132">必要に応じて、 **[コレクション]** ページの **[式]** テキスト ボックスにある参照ボタン ( **[...]** ) をクリックし、プロパティ値を更新する式を作成します。</span><span class="sxs-lookup"><span data-stu-id="85a69-132">Optionally, click the browse button **(...)** in the **Expressions** text box on the **Collection** page to create expressions that update property values.</span></span> <span data-ttu-id="85a69-133">詳細については、「 [プロパティ式を追加または変更する](expressions/add-or-change-a-property-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85a69-133">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="85a69-134">**[プロパティ]** 一覧に表示されるプロパティは、列挙子ごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="85a69-134">The properties listed in the **Property** list varies by enumerator.</span></span>  
  
7.  <span data-ttu-id="85a69-135">必要に応じて、**[変数のマッピング]** をクリックし、オブジェクトのプロパティをコレクションの値にマップします。その後、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="85a69-135">Optionally, click **Variable Mappings** to map object properties to the collection value, and then do the following:</span></span>  
  
    1.  <span data-ttu-id="85a69-136">**[変数]** 一覧で変数を選択するか、 **[\<New Variable>]** をクリックして新しい変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="85a69-136">In the **Variables** list, select a variable or click **\<New Variable>** to create a new variable.</span></span>  
  
    2.  <span data-ttu-id="85a69-137">新しい変数を追加する場合、 **[変数の追加]** ダイアログ ボックスで変数のプロパティを設定し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-137">If you add a new variable, set the variable properties in the **Add Variable** dialog box and click **OK**.</span></span>  
  
    3.  <span data-ttu-id="85a69-138">Foreach Item 列挙子を使用する場合、 **[インデックス]** の一覧で、インデックス値を更新できます。</span><span class="sxs-lookup"><span data-stu-id="85a69-138">If you use the For Each Item enumerator, you can update the index value in the **Index** list.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="85a69-139">インデックス値は、アイテム内のどの列が変数にマップされるかを示します。</span><span class="sxs-lookup"><span data-stu-id="85a69-139">The index value indicates which column in the item to map to the variable.</span></span> <span data-ttu-id="85a69-140">0 以外のインデックス値を使用できるのは、Foreach Item 列挙子だけです。</span><span class="sxs-lookup"><span data-stu-id="85a69-140">Only the For Each Item enumerator can use an index value other than 0.</span></span>  
  
8.  <span data-ttu-id="85a69-141">必要に応じて **[式]** をクリックし、 **[式]** ページで Foreach ループ コンテナーのプロパティ用のプロパティ式を作成します。</span><span class="sxs-lookup"><span data-stu-id="85a69-141">Optionally, click **Expressions** and, on the **Expressions** page, create property expressions for the properties of the Foreach Loop container.</span></span> <span data-ttu-id="85a69-142">詳細については、「 [プロパティ式を追加または変更する](expressions/add-or-change-a-property-expression.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85a69-142">For more information, see [Add or Change a Property Expression](expressions/add-or-change-a-property-expression.md).</span></span>  
  
9. <span data-ttu-id="85a69-143">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="85a69-143">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85a69-144">参照</span><span class="sxs-lookup"><span data-stu-id="85a69-144">See Also</span></span>  
 [<span data-ttu-id="85a69-145">Foreach ループ コンテナー</span><span class="sxs-lookup"><span data-stu-id="85a69-145">Foreach Loop Container</span></span>](control-flow/foreach-loop-container.md)  
  
  
