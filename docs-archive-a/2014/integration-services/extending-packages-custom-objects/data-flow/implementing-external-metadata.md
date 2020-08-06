---
title: 外部メタデータの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a6b77229c528bc08057e662a4b3761d1daf732f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713342"
---
# <a name="implementing-external-metadata"></a><span data-ttu-id="e2f4b-102">外部メタデータの実装</span><span class="sxs-lookup"><span data-stu-id="e2f4b-102">Implementing External Metadata</span></span>
  <span data-ttu-id="e2f4b-103">コンポーネントがそのデータ ソースから切断されると、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> インターフェイスを使用することによって、入力および出力列のコレクション内の列を、その外部データ ソースの列に対して検証できます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-103">When a component is disconnected from its data source, you can validate the columns in the input and output column collections against the columns at its external data source by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> interface.</span></span> <span data-ttu-id="e2f4b-104">このインターフェイスを使用すると、外部データ ソースの列のスナップショットを保持し、これらの列をコンポーネントの入力および出力列コレクションの列にマップできます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-104">This interface lets you maintain a snapshot of the columns at the external data source and map these columns to the columns in the input and output column collection of the component.</span></span>  
  
 <span data-ttu-id="e2f4b-105">外部メタデータ列を実装することで、追加した列のコレクションに対する管理と検証の必要が生じるため、コンポーネントの開発にオーバーヘッドと複雑性が加わりますが、検証のためのサーバーへのラウンド トリップに余計な費用をかけなくても済むので、開発作業は行う価値のあるものになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-105">Implementing external metadata columns adds a layer of overhead and complexity to component development, because you must maintain and validate against an additional column collection, but the ability to avoid expensive round trips to the server for validation may make this development work worthwhile.</span></span>  
  
## <a name="populating-external-metadata-columns"></a><span data-ttu-id="e2f4b-106">外部メタデータ列の設定</span><span class="sxs-lookup"><span data-stu-id="e2f4b-106">Populating External Metadata Columns</span></span>  
 <span data-ttu-id="e2f4b-107">外部メタデータ列は、通常、対応する入力または出力列を作成するときにコレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-107">External metadata columns are typically added to the collection when the corresponding input or output column is created.</span></span> <span data-ttu-id="e2f4b-108"><xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> メソッドを呼び出して、新しい列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-108">New columns are created by calling the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> method.</span></span> <span data-ttu-id="e2f4b-109">次に、外部データ ソースに一致するように列のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-109">The properties of the column are then set to match the external data source.</span></span>  
  
 <span data-ttu-id="e2f4b-110">外部メタデータ列を対応する入力または出力列にマップするには、外部メタデータ列の ID を入力または出力列の <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-110">The external metadata column is mapped to the corresponding input or output column by assigning the ID of the external metadata column to the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property of the input or output column.</span></span> <span data-ttu-id="e2f4b-111">これにより、コレクションの <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> メソッドを使用して、特定の入力列または出力列に対する外部メタデータ列を簡単に探すことができます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-111">This lets you locate the external metadata column easily for a specific input or output column by using the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> method of the collection.</span></span>  
  
 <span data-ttu-id="e2f4b-112">次の例では、外部メタデータ列を作成し、<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> プロパティを設定することによって出力列にマップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-112">The following example shows how to create an external metadata column and then map the column to an output column by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> property.</span></span>  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a><span data-ttu-id="e2f4b-113">外部メタデータ列での検証</span><span class="sxs-lookup"><span data-stu-id="e2f4b-113">Validating with External Metadata Columns</span></span>  
 <span data-ttu-id="e2f4b-114">検証を行うには、外部メタデータ列のコレクションを保持するための手順をコンポーネントに追加する必要があります。追加された列のコレクションに対して検証を行う必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-114">Validation requires additional steps for components that maintain an external metadata column collection, because you must validate against an additional collection of columns.</span></span> <span data-ttu-id="e2f4b-115">検証は、接続された状態での検証と切断された状態での検証に分けられます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-115">Validation can be divided into connected validation or disconnected validation.</span></span>  
  
### <a name="connected-validation"></a><span data-ttu-id="e2f4b-116">接続された状態での検証</span><span class="sxs-lookup"><span data-stu-id="e2f4b-116">Connected Validation</span></span>  
 <span data-ttu-id="e2f4b-117">コンポーネントが外部データ ソースに接続されると、入力または出力コレクション内の列は、外部データ ソースに対して直接検証されます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-117">When a component is connected to an external data source, the columns in the input or output collections are verified directly against the external data source.</span></span> <span data-ttu-id="e2f4b-118">また、外部メタデータのコレクション内の列を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-118">Additionally, the columns in the external metadata collection must be validated.</span></span> <span data-ttu-id="e2f4b-119">外部メタデータのコレクションは [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] の **[詳細エディター]** による変更が可能なうえに、それによってコレクションに行われた変更は検出できないため、この検証が必要となります。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-119">This is required because the external metadata collection can be modified by using the **Advanced Editor** in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], and changes made to the collection are not detectable.</span></span> <span data-ttu-id="e2f4b-120">したがって、接続された状態のコンポーネントでは、外部メタデータ列のコレクション内の列が外部データ ソースの列を継続して反映していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-120">Therefore, when connected, components must make sure that the columns in the external metadata column collection continue to reflect the columns at the external data source.</span></span>  
  
 <span data-ttu-id="e2f4b-121">コレクションのプロパティをに設定することによって、**詳細エディター**内の外部メタデータコレクションを非表示にすることができ <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> `false` ます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-121">You may choose to hide the external metadata collection in the **Advanced Editor** by setting the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> property of the collection to `false`.</span></span> <span data-ttu-id="e2f4b-122">ただし、この設定を行うと、入力または出力コレクションの列を外部メタデータ列のコレクションの列にマップするために使用する、エディターの **[列マッピング]** タブも非表示になります。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-122">However this also hides the **Column Mapping** tab of the editor, which lets users map columns from the input or output collection to the columns in the external metadata column collection.</span></span> <span data-ttu-id="e2f4b-123">このプロパティを `false` に設定すると、開発者のプログラムによるコレクションの変更を妨げることなく、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でのみ使用されるコンポーネントの、外部メタデータ列のコレクションをある程度保護できます。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-123">Setting this property to `false` does not prevent developers from programmatically modifying the collection, but it does provide a level of protection for the external metadata column collection of a component that is used exclusively in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="disconnected-validation"></a><span data-ttu-id="e2f4b-124">切断された状態での検証</span><span class="sxs-lookup"><span data-stu-id="e2f4b-124">Disconnected Validation</span></span>  
 <span data-ttu-id="e2f4b-125">コンポーネントが外部データ ソースから切断されている場合、検証は簡略化されます。これは、外部ソースに対してではなく、外部メタデータのコレクション内の列に対して、入力または出力コレクション内の列が直接検証されるためです。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-125">When a component is disconnected from an external data source, validation is simplified because the columns in the input or output collection are verified directly against the columns in the external metadata collection and not against the external source.</span></span> <span data-ttu-id="e2f4b-126">コンポーネントの外部データ ソースへの接続が確立されていない場合、または <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> プロパティが `false` の場合は、コンポーネントは切断された状態での検証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-126">A component should perform disconnected validation when the connection to its external data source has not been established, or when the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="e2f4b-127">次のコード例は、コンポーネントの外部メタデータ列のコレクションに対し、検証を実行するコンポーネントの実装です。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-127">The following code example demonstrates an implementation of a component that performs validation against its external metadata column collection.</span></span>  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  
  
<span data-ttu-id="e2f4b-128">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="e2f4b-128">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e2f4b-129">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-129">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e2f4b-130">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="e2f4b-130">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e2f4b-131">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="e2f4b-131">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f4b-132">参照</span><span class="sxs-lookup"><span data-stu-id="e2f4b-132">See Also</span></span>  
 [<span data-ttu-id="e2f4b-133">データ フロー</span><span class="sxs-lookup"><span data-stu-id="e2f4b-133">Data Flow</span></span>](../../data-flow/data-flow.md)  
  
  
