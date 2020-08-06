---
title: スクリプト コンポーネントに対するエラー出力のシミュレート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], error output
- error outputs [Integration Services], Script component
ms.assetid: f8b6ecff-ac99-4231-a0e7-7ce4ad76bad0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bed458ce378eb26cd863811b4974b5f39429e1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713314"
---
# <a name="simulating-an-error-output-for-the-script-component"></a><span data-ttu-id="c3ca8-102">スクリプト コンポーネントに対するエラー出力のシミュレート</span><span class="sxs-lookup"><span data-stu-id="c3ca8-102">Simulating an Error Output for the Script Component</span></span>
  <span data-ttu-id="c3ca8-103">エラー行の自動処理のスクリプト コンポーネントでエラー出力として出力を直接構成することはできませんが、別の出力を作成するか、可能な場合はスクリプトで条件ロジックを使用してこの出力に行を送信することによって、組み込みエラー出力の機能を再現することができます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-103">Although you cannot directly configure an output as an error output in the Script component for automatic handling of error rows, you can reproduce the functionality of a built-in error output by creating an additional output and using conditional logic in your script to direct rows to this output when appropriate.</span></span> <span data-ttu-id="c3ca8-104">2 つの出力列を追加してエラー番号、およびエラーが発生した列の ID を受け取ることにより、組み込みエラー出力の動作を模倣することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-104">You may want to imitate the behavior of a built-in error output by adding two additional output columns to receive the error number and the ID of the column in which an error occurred.</span></span>  
  
 <span data-ttu-id="c3ca8-105">事前定義された特定の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラー コードに対応するエラーの説明を追加する場合は、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> インターフェイスの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> メソッドを使用できます。これは、スクリプト コンポーネントの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティから使用できます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-105">If you want to add the error description that corresponds to a specific predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] error code, you can use the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.GetErrorDescription%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface, available through the Script component's <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3ca8-106">例</span><span class="sxs-lookup"><span data-stu-id="c3ca8-106">Example</span></span>  
 <span data-ttu-id="c3ca8-107">次に示す例では、2 つの同期出力を持つ変換として構成された、スクリプト コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-107">The example shown here uses a Script component configured as a transformation that has two synchronous outputs.</span></span> <span data-ttu-id="c3ca8-108">このスクリプト コンポーネントの目的は、AdventureWorks サンプル データベースの住所データから、エラー行をフィルター選択することです。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-108">The purpose of the Script component is to filter error rows from address data in the AdventureWorks sample database.</span></span> <span data-ttu-id="c3ca8-109">この架空の例では、北米の顧客向けプロモーションを準備中であり、北米以外の住所をフィルターによって除外する必要があるものとします。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-109">This fictitious example assumes that we are preparing a promotion for North American customers and need to filter out addresses that are not located in North America.</span></span>  
  
#### <a name="to-configure-the-example"></a><span data-ttu-id="c3ca8-110">例を構成するには</span><span class="sxs-lookup"><span data-stu-id="c3ca8-110">To configure the example</span></span>  
  
1.  <span data-ttu-id="c3ca8-111">新しいスクリプト コンポーネントの作成前に、接続マネージャーを作成し、AdventureWorks サンプル データベースから住所データを選択するデータ フローの変換元を構成します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-111">Before creating the new Script component, create a connection manager and configure a data flow source that selects address data from the AdventureWorks sample database.</span></span> <span data-ttu-id="c3ca8-112">この例では CountryRegionName 列のみを調べるので、単純に Person.vStateCountryProvinceRegion ビューを使用できます。また、Person.Address、Person.StateProvince、および Person.CountryRegion の表を結合して、データを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-112">For this example, which only looks at the CountryRegionName column, you can simply use the Person.vStateCountryProvinceRegion view, or you can select data by joining the Person.Address, Person.StateProvince, and Person.CountryRegion tables.</span></span>  
  
2.  <span data-ttu-id="c3ca8-113">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換として構成します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-113">Add a new Script component to the Data Flow designer surface and configure it as a transformation.</span></span> <span data-ttu-id="c3ca8-114">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-114">Open the **Script Transformation Editor**.</span></span>  
  
3.  <span data-ttu-id="c3ca8-115">**[スクリプト]** ページの **[ScriptLanguage]** プロパティに、スクリプトのコード作成に使用するスクリプト言語を設定します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-115">On the **Script** page, set the **ScriptLanguage** property to the script language that you want to use to code the script.</span></span>  
  
4.  <span data-ttu-id="c3ca8-116">**[スクリプトの編集]** をクリックして、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) を開きます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-116">Click **Edit Script** to open [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
5.  <span data-ttu-id="c3ca8-117">`Input0_ProcessInputRow` メソッドに、以下に示すサンプル コードを入力するか貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-117">In the `Input0_ProcessInputRow` method, type or paste the sample code shown below.</span></span>  
  
6.  <span data-ttu-id="c3ca8-118">VSTA を閉じます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-118">Close VSTA.</span></span>  
  
7.  <span data-ttu-id="c3ca8-119">**[入力列]** ページで、スクリプト変換で処理する列を選択します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-119">On the **Input Columns** page, select the columns that you want to process in the Script transformation.</span></span> <span data-ttu-id="c3ca8-120">この例では CountryRegionName 列のみを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-120">This example uses only the CountryRegionName column.</span></span> <span data-ttu-id="c3ca8-121">選択しなかった使用可能な入力列は、データ フロー内で変更されず、そのまま渡されます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-121">Available input columns that you leave unselected will simply be passed through unchanged in the data flow.</span></span>  
  
8.  <span data-ttu-id="c3ca8-122">[**入力および出力**] ページで、新しい2番目の出力を追加し、その `SynchronousInputID` 値を入力の ID に設定します。これは、 `SynchronousInputID` 既定の出力のプロパティの値でもあります。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-122">On the **Inputs and Outputs** page, add a new, second output, and set its `SynchronousInputID` value to the ID of the input, which is also the value of the `SynchronousInputID` property of the default output.</span></span> <span data-ttu-id="c3ca8-123">両方の出力の `ExclusionGroup` プロパティを 0 以外の同じ値 (たとえば 1) に設定し、各行が 2 つの出力のうち一方のみに送られるようにします。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-123">Set the `ExclusionGroup` property of both outputs to the same non-zero value (for example, 1) to indicate that each row will be directed to only one of the two outputs.</span></span> <span data-ttu-id="c3ca8-124">新しいエラー出力に、"MyErrorOutput" などのわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-124">Give the new error output a distinctive name, such as "MyErrorOutput."</span></span>  
  
9. <span data-ttu-id="c3ca8-125">必要なエラー情報を取得するため、追加の出力列を新しいエラー出力に追加します。エラー コード、エラーが発生した列の ID、エラーの説明などを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-125">Add additional output columns to the new error output to capture the desired error information, which may include the error code, the ID of the column in which the error occurred, and possibly the error description.</span></span> <span data-ttu-id="c3ca8-126">この例では、新しい列 ErrorColumn および ErrorMessage を作成しています。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-126">This example creates the new columns, ErrorColumn and ErrorMessage.</span></span> <span data-ttu-id="c3ca8-127">事前定義された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] エラーを独自の実装で検出する場合、エラー番号用の ErrorCode 列を必ず追加してください。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-127">If you are catching predefined [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] errors in your own implementation, make sure to add an ErrorCode column for the error number.</span></span>  
  
10. <span data-ttu-id="c3ca8-128">スクリプト コンポーネントがエラー状態を確認する入力列 (複数の場合もある) の ID 値を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-128">Note the ID value of the input column or columns that the Script component will check for error conditions.</span></span> <span data-ttu-id="c3ca8-129">この例では、この列 ID を使用して ErrorColumn 値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-129">This example uses this column identifier to populate the ErrorColumn value.</span></span>  
  
11. <span data-ttu-id="c3ca8-130">**[スクリプト変換エディター]** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-130">Close the **Script Transformation Editor.**</span></span>  
  
12. <span data-ttu-id="c3ca8-131">スクリプト コンポーネントの出力を、適切な変換先にアタッチします。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-131">Attach the outputs of the Script component to suitable destinations.</span></span> <span data-ttu-id="c3ca8-132">アドホック テスト用に最も構成しやすいのは、フラット ファイル変換先です。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-132">Flat file destinations are the easiest to configure for ad hoc testing.</span></span>  
  
13. <span data-ttu-id="c3ca8-133">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-133">Run the package.</span></span>  
  
```vb  
Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
  
  If Row.CountryRegionName <> "Canada" _  
      And Row.CountryRegionName <> "United States" Then  
  
    Row.ErrorColumn = 68 ' ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America."  
    Row.DirectRowToMyErrorOutput()  
  
  Else  
  
    Row.DirectRowToOutput0()  
  
  End If  
  
End Sub  
```  
  
```csharp  
public override void Input0_ProcessInputRow(Input0Buffer Row)  
{  
  
  if (Row.CountryRegionName!="Canada"&&Row.CountryRegionName!="United States")  
  
  {  
    Row.ErrorColumn = 68; // ID of CountryRegionName column  
    Row.ErrorMessage = "Address is not in North America.";  
    Row.DirectRowToMyErrorOutput();  
  
  }  
  else  
  {  
  
    Row.DirectRowToOutput0();  
  
  }  
  
}  
```  
  
<span data-ttu-id="c3ca8-134">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="c3ca8-134">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c3ca8-135">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-135">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c3ca8-136">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="c3ca8-136">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c3ca8-137">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c3ca8-137">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ca8-138">参照</span><span class="sxs-lookup"><span data-stu-id="c3ca8-138">See Also</span></span>  
 <span data-ttu-id="c3ca8-139">[データのエラー処理](../data-flow/error-handling-in-data.md) </span><span class="sxs-lookup"><span data-stu-id="c3ca8-139">[Error Handling in Data](../data-flow/error-handling-in-data.md) </span></span>  
 <span data-ttu-id="c3ca8-140">[データフローコンポーネントでのエラー出力の使用](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span><span class="sxs-lookup"><span data-stu-id="c3ca8-140">[Using Error Outputs in a Data Flow Component](../extending-packages-custom-objects/data-flow/using-error-outputs-in-a-data-flow-component.md) </span></span>  
 [<span data-ttu-id="c3ca8-141">スクリプト コンポーネントによる同期変換の作成</span><span class="sxs-lookup"><span data-stu-id="c3ca8-141">Creating a Synchronous Transformation with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md) 
  
  
