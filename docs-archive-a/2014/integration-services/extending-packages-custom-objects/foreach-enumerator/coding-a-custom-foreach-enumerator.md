---
title: カスタム Foreach 列挙子のコーディング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom foreach enumerators [Integration Services], coding
ms.assetid: 279cf6de-d06f-40e7-b8ca-569310449f36
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b7e6c16124f4682dbdc98f602417bf8f68ce099
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633912"
---
# <a name="coding-a-custom-foreach-enumerator"></a><span data-ttu-id="f074d-102">カスタム Foreach 列挙子のコーディング</span><span class="sxs-lookup"><span data-stu-id="f074d-102">Coding a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="f074d-103"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f074d-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="f074d-104">カスタム列挙子の実際のサンプルについては、「[カスタム ForEach 列挙子用ユーザー インターフェイスの開発](developing-a-user-interface-for-a-custom-foreach-enumerator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f074d-104">For a working sample of a custom enumerator, see [Developing a User Interface for a Custom ForEach Enumerator](developing-a-user-interface-for-a-custom-foreach-enumerator.md).</span></span>  
  
## <a name="initializing-the-enumerator"></a><span data-ttu-id="f074d-105">列挙子の初期化</span><span class="sxs-lookup"><span data-stu-id="f074d-105">Initializing the Enumerator</span></span>  
 <span data-ttu-id="f074d-106"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> メソッドをオーバーライドして、パッケージで定義されている接続マネージャーへの参照と、エラー、警告、および情報メッセージを発生させるために使用できるイベント インターフェイスへの参照をキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="f074d-106">You can override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.InitializeForEachEnumerator%2A> method to cache references to the connection managers defined in the package, and to cache references to the events interface that you can use to raise errors, warnings, and informational messages.</span></span>  
  
## <a name="validating-the-enumerator"></a><span data-ttu-id="f074d-107">列挙子の検証</span><span class="sxs-lookup"><span data-stu-id="f074d-107">Validating the Enumerator</span></span>  
 <span data-ttu-id="f074d-108"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> メソッドをオーバーライドして、列挙子が正しく構成されているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="f074d-108">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> method to verify that the enumerator is correctly configured.</span></span> <span data-ttu-id="f074d-109">メソッドの `Failure` を返す場合、列挙子および列挙子を含むパッケージは実行されません。</span><span class="sxs-lookup"><span data-stu-id="f074d-109">If the method returns `Failure`, the enumerator and the package that contains the enumerator will not be executed.</span></span> <span data-ttu-id="f074d-110">このメソッドの実装方法は列挙子ごとに異なりますが、列挙子が <xref:Microsoft.SqlServer.Dts.Runtime.Variable> オブジェクトまたは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> オブジェクトに依存する場合は、メソッドに渡されたコレクション内に、これらのオブジェクトが存在することを検証するためのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f074d-110">The implementation of this method is specific to each enumerator, but if the enumerator relies on <xref:Microsoft.SqlServer.Dts.Runtime.Variable> or <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> objects, you should add code to verify that these objects exist in the collections that are provided to the method.</span></span>  
  
 <span data-ttu-id="f074d-111">次のコード例では、列挙子のプロパティで指定された変数を確認するために <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f074d-111">The following code example demonstrates an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.Validate%2A> that checks for a variable specified in a property of the enumerator.</span></span>  
  
```csharp  
private string variableNameValue;  
  
public string VariableName  
{  
    get{ return this.variableNameValue; }  
    set{ this.variableNameValue = value; }  
}  
  
public override DTSExecResult Validate(Connections connections, VariableDispenser variableDispenser, IDTSInfoEvents infoEvents, IDTSLogging log)  
{  
    if (!variableDispenser.Contains(this.variableNameValue))  
    {  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + this.variableNameValue + " does not exist in the collection.", "", 0);  
            return DTSExecResult.Failure;  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Private variableNameValue As String  
  
Public Property VariableName() As String  
    Get   
         Return Me.variableNameValue  
    End Get  
    Set (ByVal Value As String)   
         Me.variableNameValue = value  
    End Set  
End Property  
  
Public Overrides Function Validate(ByVal connections As Connections, ByVal variableDispenser As VariableDispenser, ByVal infoEvents As IDTSInfoEvents, ByVal log As IDTSLogging) As DTSExecResult  
    If Not variableDispenser.Contains(Me.variableNameValue) Then  
        infoEvents.FireError(0, "MyEnumerator", "The Variable " + Me.variableNameValue + " does not exist in the collection.", "", 0)  
            Return DTSExecResult.Failure  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
## <a name="returning-the-collection"></a><span data-ttu-id="f074d-112">コレクションを返す処理</span><span class="sxs-lookup"><span data-stu-id="f074d-112">Returning the Collection</span></span>  
 <span data-ttu-id="f074d-113">実行中は、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> コンテナーが、カスタム列挙子の <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f074d-113">During execution, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="f074d-114">このメソッドでは、列挙子はアイテムのコレクションを作成し、値を設定して返します。</span><span class="sxs-lookup"><span data-stu-id="f074d-114">In this method, the enumerator creates and populates its collection of items, and then returns the collection.</span></span> <span data-ttu-id="f074d-115">次に、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> はコレクション内のアイテムを繰り返し、各アイテムの制御フローを実行します。</span><span class="sxs-lookup"><span data-stu-id="f074d-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates the items in the collection, and executes its control flow for each item in the collection.</span></span>  
  
 <span data-ttu-id="f074d-116">次に、ランダムな整数の配列を返す <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> の実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="f074d-116">The following example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> that returns an array of random integers.</span></span>  
  
```csharp  
public override object GetEnumerator()  
{  
    ArrayList numbers = new ArrayList();  
  
    Random randomNumber = new Random(DateTime.Now);  
  
    for( int x=0; x < 100; x++ )  
        numbers.Add( randomNumber.Next());  
  
    return numbers;  
}  
```  
  
```vb  
Public Overrides Function GetEnumerator() As Object  
    Dim numbers As ArrayList =  New ArrayList()   
  
    Dim randomNumber As Random =  New Random(DateTime.Now)   
  
        Dim x As Integer  
        For  x = 0 To  100- 1  Step  x + 1  
        numbers.Add(randomNumber.Next())  
        Next  
  
    Return numbers  
End Function  
```  
  
<span data-ttu-id="f074d-117">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="f074d-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="f074d-118">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f074d-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="f074d-119">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="f074d-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="f074d-120">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="f074d-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f074d-121">参照</span><span class="sxs-lookup"><span data-stu-id="f074d-121">See Also</span></span>  
 <span data-ttu-id="f074d-122">[カスタム Foreach 列挙子の作成](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="f074d-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="f074d-123">カスタム ForEach 列挙子用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="f074d-123">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
