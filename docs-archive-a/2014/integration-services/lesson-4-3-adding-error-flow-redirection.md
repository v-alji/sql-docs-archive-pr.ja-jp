---
title: '手順 3 : エラー フロー リダイレクトの追加 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5683a45d-9e73-4cd5-83ca-fae8b26b488c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ceaea310cba05a940f310c01b52d5f912a53bea8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640139"
---
# <a name="step-3-adding-error-flow-redirection"></a><span data-ttu-id="96832-102">手順 3:エラー フロー リダイレクトの追加</span><span class="sxs-lookup"><span data-stu-id="96832-102">Step 3: Adding Error Flow Redirection</span></span>
  <span data-ttu-id="96832-103">前の実習で学んだように、Lookup Currency Key 変換で壊れているサンプル フラット ファイルを処理しようとするとエラーが発生し、変換を行うことができません。</span><span class="sxs-lookup"><span data-stu-id="96832-103">As demonstrated in the previous task, the Lookup Currency Key transformation cannot generate a match when the transformation tries to process the corrupted sample flat file, which produced an error.</span></span> <span data-ttu-id="96832-104">この変換ではエラー出力に既定の設定を使用するため、エラーが発生すると変換は失敗します。</span><span class="sxs-lookup"><span data-stu-id="96832-104">Because the transformation uses the default settings for error output, any error causes the transformation to fail.</span></span> <span data-ttu-id="96832-105">変換が失敗すると、それ以降のパッケージも失敗します。</span><span class="sxs-lookup"><span data-stu-id="96832-105">When the transformation fails, the rest of the package also fails.</span></span>  
  
 <span data-ttu-id="96832-106">エラー出力を使用し、失敗した行を別の処理パスにリダイレクトするようにコンポーネントを構成することで、変換の失敗を回避できます。</span><span class="sxs-lookup"><span data-stu-id="96832-106">Instead of permitting the transformation to fail, you can configure the component to redirect the failed row to another processing path by using the error output.</span></span> <span data-ttu-id="96832-107">別のエラー処理パスを使用すると、さまざまな処理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="96832-107">Use of a separate error processing path lets you do a number of things.</span></span> <span data-ttu-id="96832-108">たとえば、データを消去した後に失敗した行を再処理できます。</span><span class="sxs-lookup"><span data-stu-id="96832-108">For instance, you might try to clean the data and then reprocess the failed row.</span></span> <span data-ttu-id="96832-109">失敗した行を詳細なエラー情報と共に保存し、後の検証や再処理に役立てることも可能です。</span><span class="sxs-lookup"><span data-stu-id="96832-109">Or, you might save the failed row along with additional error information for later verification and reprocessing.</span></span>  
  
 <span data-ttu-id="96832-110">ここでは、失敗した行をエラー出力にリダイレクトするよう Lookup Currency Key 変換を構成します。</span><span class="sxs-lookup"><span data-stu-id="96832-110">In this task, you will configure the Lookup Currency Key transformation to redirect any rows that fail to the error output.</span></span> <span data-ttu-id="96832-111">データ フローのエラー分岐では、失敗した行はファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="96832-111">In the error branch of the data flow, these rows will be written to a file.</span></span>  
  
 <span data-ttu-id="96832-112">既定では、エラー出力の2つの追加列 ( [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] **ErrorCode**と**errorcolumn**) には、エラー番号を表す数値コードと、エラーが発生した列の ID だけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="96832-112">By default the two extra columns in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] error output, **ErrorCode** and **ErrorColumn**, contain only numeric codes that represent an error number, and the ID of the column in which the error occurred.</span></span> <span data-ttu-id="96832-113">これらの数値は、対応するエラー説明がないとあまり役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="96832-113">These numeric values may be of limited use without the corresponding error description.</span></span>  
  
 <span data-ttu-id="96832-114">エラー出力の有用性を高めるには、パッケージによって失敗行がファイルに書き込まれる前に、スクリプト コンポーネントを使用して [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API にアクセスし、エラーの説明を取得します。</span><span class="sxs-lookup"><span data-stu-id="96832-114">To enhance the usefulness of the error output, before the package writes the failed rows to the file, you will use a Script component to access the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] API and get a description of the error.</span></span>  
  
### <a name="to-configure-an-error-output"></a><span data-ttu-id="96832-115">エラー出力を構成するには</span><span class="sxs-lookup"><span data-stu-id="96832-115">To configure an error output</span></span>  
  
1.  <span data-ttu-id="96832-116">[ **SSIS ツールボックス**] で **[共通**] を展開し、[**スクリプトコンポーネント**] を [**データフロー** ] タブのデザイン画面にドラッグします。 [ **Lookup Currency Key** ] 変換の右側に**スクリプト**を配置します。</span><span class="sxs-lookup"><span data-stu-id="96832-116">In the **SSIS Toolbox**, expand **Common**, and then drag **Script Component** onto the design surface of the **Data Flow** tab. Place **Script** to the right of the **Lookup Currency Key** transformation.</span></span>  
  
2.  <span data-ttu-id="96832-117">**[スクリプト コンポーネントの種類を選択]** ダイアログ ボックスで、 **[変換]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96832-117">In the **Select Script Component Type** dialog box, click **Transformation**, and click **OK**.</span></span>  
  
3.  <span data-ttu-id="96832-118">**[Lookup Currency Key]** 変換をクリックします。赤色の矢印を、新しく追加した **[スクリプト]** 変換までドラッグして、これら 2 つのコンポーネントを接続します。</span><span class="sxs-lookup"><span data-stu-id="96832-118">Click the **Lookup Currency Key** transformation and then drag the red arrow onto the newly added **Script** transformation to connect the two components.</span></span>  
  
     <span data-ttu-id="96832-119">赤い矢印は、 **[Lookup Currency Key]** 変換のエラー出力を表します。</span><span class="sxs-lookup"><span data-stu-id="96832-119">The red arrow represents the error output of the **Lookup Currency Key** transformation.</span></span> <span data-ttu-id="96832-120">赤い矢印を使用して変換をスクリプト コンポーネントに接続すると、エラー処理をスクリプト コンポーネントにリダイレクトできます。スクリプト コンポーネントではエラーが処理され、変換先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="96832-120">By using the red arrow to connect the transformation to the Script component, you can redirect any processing errors to the Script component, which then processes the errors and sends them to the destination.</span></span>  
  
4.  <span data-ttu-id="96832-121">**[エラー出力の構成]** ダイアログ ボックスの **[エラー]** 列で、 **[行のリダイレクト]** を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96832-121">In the **Configure Error Output** dialog box, in the **Error** column, select **Redirect row**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="96832-122">**[データ フロー]** デザイン画面で、新しく追加した **[スクリプト コンポーネント]** で **[スクリプト コンポーネント]** をクリックし、名前を「 **Get Error Description**」に変更します。</span><span class="sxs-lookup"><span data-stu-id="96832-122">On the **Data Flow** design surface, click **Script Component** in the newly added **ScriptComponent**, and change the name to **Get Error Description**.</span></span>  
  
6.  <span data-ttu-id="96832-123">**[Get Error Description]** 変換をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="96832-123">Double-click the **Get Error Description** transformation.</span></span>  
  
7.  <span data-ttu-id="96832-124">**[スクリプト変換エディター]** ダイアログ ボックスの **[入力列]** ページで、 **[ErrorCode]** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="96832-124">In the **Script Transformation Editor** dialog box, on the **Input Columns** page, select the **ErrorCode** column.</span></span>  
  
8.  <span data-ttu-id="96832-125">**[入力および出力]** ページで **[出力 0]** を展開し、 **[出力列]** をクリックして、 **[列の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96832-125">On the **Inputs and Outputs** page, expand **Output 0**, click **Output Columns**, and then click **Add Column**.</span></span>  
  
9. <span data-ttu-id="96832-126">プロパティに `Name` 「 **ErrorDescription** 」と入力し、 `DataType` プロパティを**Unicode 文字列 [DT_WSTR]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="96832-126">In the `Name` property, type **ErrorDescription** and set the `DataType` property to **Unicode string [DT_WSTR]**.</span></span>  
  
10. <span data-ttu-id="96832-127">[**スクリプト**] ページで、 `LocaleID` プロパティが**英語 (米国**に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="96832-127">On the **Script** page, verify that the `LocaleID` property is set to **English (United States.**</span></span>  
  
11. <span data-ttu-id="96832-128">**[スクリプトの編集]** をクリックして、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) を開きます。</span><span class="sxs-lookup"><span data-stu-id="96832-128">Click **Edit Script** to open [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="96832-129">`Input0_ProcessInputRow` メソッドに、次のコードを入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="96832-129">In the `Input0_ProcessInputRow` method, type or paste the following code.</span></span>  
  
     <span data-ttu-id="96832-130">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="96832-130">[Visual Basic]</span></span>  
  
    ```  
    Row.ErrorDescription =   
      Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
    ```  
  
     <span data-ttu-id="96832-131">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="96832-131">[Visual C#]</span></span>  
  
    ```  
    Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
    ```  
  
     <span data-ttu-id="96832-132">完成したサブルーチンのコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="96832-132">The completed subroutine will look like the following code.</span></span>  
  
     <span data-ttu-id="96832-133">[Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="96832-133">[Visual Basic]</span></span>  
  
    ```  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
      Row.ErrorDescription =   
        Me.ComponentMetaData.GetErrorDescription(Row.ErrorCode)  
  
    End Sub  
    ```  
  
     <span data-ttu-id="96832-134">[Visual C#]</span><span class="sxs-lookup"><span data-stu-id="96832-134">[Visual C#]</span></span>  
  
    ```  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
        {  
  
            Row.ErrorDescription = this.ComponentMetaData.GetErrorDescription(Row.ErrorCode);  
  
        }  
    ```  
  
12. <span data-ttu-id="96832-135">**[ビルド]** メニューの **[ソリューションのビルド]** をクリックし、スクリプトをビルドして変更を保存し、VSTA を閉じます。</span><span class="sxs-lookup"><span data-stu-id="96832-135">On the **Build** menu, click **Build Solution** to build the script and save your changes, and then close VSTA.</span></span>  
  
13. <span data-ttu-id="96832-136">**[OK]** をクリックして、 **[スクリプト変換エディター]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="96832-136">Click **OK** to close the **Script Transformation Editor** dialog box.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="96832-137">次の手順</span><span class="sxs-lookup"><span data-stu-id="96832-137">Next Steps</span></span>  
 <span data-ttu-id="96832-138">[手順 4: フラットファイル変換先の追加](lesson-4-4-adding-a-flat-file-destination.md</span><span class="sxs-lookup"><span data-stu-id="96832-138">[Step 4: Adding a Flat File Destination](lesson-4-4-adding-a-flat-file-destination.md</span></span>  
  
  
