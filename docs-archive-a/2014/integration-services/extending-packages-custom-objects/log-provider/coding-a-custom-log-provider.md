---
title: カスタム ログ プロバイダーのコーディング | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom log providers [Integration Services], coding
ms.assetid: 979a29ca-956e-4fdd-ab47-f06e84cead7a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5d529420207ac065ae5ecb3c1d984de3021845b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716422"
---
# <a name="coding-a-custom-log-provider"></a><span data-ttu-id="3dd1c-102">カスタム ログ プロバイダーのコーディング</span><span class="sxs-lookup"><span data-stu-id="3dd1c-102">Coding a Custom Log Provider</span></span>
  <span data-ttu-id="3dd1c-103"><xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスを継承するクラスを作成し、<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性をそのクラスに適用したら、基本クラスのプロパティとメソッドの実装をオーバーライドして、カスタム機能を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-103">After you have created a class that inherits from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, and applied the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class, you must override the implementation of the properties and methods of the base class to provide your custom functionality.</span></span>  
  
 <span data-ttu-id="3dd1c-104">カスタム ログ プロバイダーの実際のサンプルが必要であれば、「[カスタム ログ プロバイダー用ユーザー インターフェイスの開発](developing-a-user-interface-for-a-custom-log-provider.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-104">For working samples of custom log providers, see [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md).</span></span>  
  
## <a name="configuring-the-log-provider"></a><span data-ttu-id="3dd1c-105">ログ プロバイダーの構成</span><span class="sxs-lookup"><span data-stu-id="3dd1c-105">Configuring the Log Provider</span></span>  
  
### <a name="initializing-the-log-provider"></a><span data-ttu-id="3dd1c-106">ログ プロバイダーの初期化</span><span class="sxs-lookup"><span data-stu-id="3dd1c-106">Initializing the Log Provider</span></span>  
 <span data-ttu-id="3dd1c-107"><xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> メソッドをオーバーライドして、接続のコレクションおよびイベント インターフェイスへの参照をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-107">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.InitializeLogProvider%2A> method to cache references to the connections collection and the events interface.</span></span> <span data-ttu-id="3dd1c-108">キャッシュした参照は、後でログ プロバイダーの他のメソッドで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-108">You can use these cached references later in other methods of the log provider.</span></span>  
  
### <a name="using-the-configstring-property"></a><span data-ttu-id="3dd1c-109">ConfigString プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="3dd1c-109">Using the ConfigString Property</span></span>  
 <span data-ttu-id="3dd1c-110">デザイン時に、ログ プロバイダーは **[構成]** 列から構成情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-110">At design time, a log provider receives configuration information from the **Configuration** column.</span></span> <span data-ttu-id="3dd1c-111">この構成情報は、ログ プロバイダーの <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティに対応しています。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-111">This configuration information corresponds to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property of the log provider.</span></span> <span data-ttu-id="3dd1c-112">既定では、この列には任意の文字列情報を取得可能なテキスト ボックスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-112">By default, this column contains a text box from which you can retrieve any string information.</span></span> <span data-ttu-id="3dd1c-113">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に含まれているほとんどのログ プロバイダーは、このプロパティを使用して、外部データ ソースに接続するためにプロバイダーが使用する接続マネージャーの名前を格納します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-113">Most of the log providers included with [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] use this property to store the name of the connection manager that the provider uses to connect to an external data source.</span></span> <span data-ttu-id="3dd1c-114">ログ プロバイダーで <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティを使用する場合は、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> メソッドを使用して、このプロパティが正しく設定されていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-114">If your log provider uses the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property, use the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to validate this property and make sure that the property is set correctly.</span></span>  
  
### <a name="validating-the-log-provider"></a><span data-ttu-id="3dd1c-115">ログ プロバイダーの検証</span><span class="sxs-lookup"><span data-stu-id="3dd1c-115">Validating the Log Provider</span></span>  
 <span data-ttu-id="3dd1c-116"><xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> メソッドをオーバーライドして、プロバイダーが正しく構成され、実行の準備ができていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method to make sure that the provider has been configured correctly and is ready for execution.</span></span> <span data-ttu-id="3dd1c-117">通常、少なくとも <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> が正しく設定されていることを検証します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-117">Typically, a minimum level of validation is to make sure that the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> is set correctly.</span></span> <span data-ttu-id="3dd1c-118">ログ プロバイダーが <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> メソッドから <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> を返すまでは、実行を続行できません。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-118">Execution cannot continue until the log provider returns <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult.Success> from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="3dd1c-119">次のコード例では、接続マネージャーの名前が指定され、パッケージに接続マネージャーが存在し、接続マネージャーが <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> プロパティにファイル名を返すことを確認する、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-119">The following code example shows an implementation of <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Validate%2A> that makes sure that the name of a connection manager name is specified, that the connection manager exists in the package, and that the connection manager returns a file name in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override DTSExecResult Validate(IDTSInfoEvents infoEvents)  
{  
    if (this.ConfigString.Length == 0 || connections.Contains(ConfigString) == false)  
    {  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
        return DTSExecResult.Failure;  
    }  
    else  
    {  
        string fileName = connections[ConfigString].AcquireConnection(null) as string;  
  
        if (fileName == null || fileName.Length == 0)  
        {  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0);  
            return DTSExecResult.Failure;  
        }  
    }  
    return DTSExecResult.Success;  
}  
```  
  
```vb  
Public Overrides Function Validate(ByVal infoEvents As IDTSInfoEvents) As DTSExecResult  
    If Me.ConfigString.Length = 0 Or connections.Contains(ConfigString) = False Then  
        infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
        Return DTSExecResult.Failure  
    Else   
        Dim fileName As String =  connections(ConfigString).AcquireConnectionCType(as string, Nothing)  
  
        If fileName = Nothing Or fileName.Length = 0 Then  
            infoEvents.FireError(0, "MyTextLogProvider", "The ConnectionManager " + ConfigString + " specified in the ConfigString property cannot be found in the collection.", "", 0)  
            Return DTSExecResult.Failure  
        End If  
    End If  
    Return DTSExecResult.Success  
End Function  
```  
  
### <a name="persisting-the-log-provider"></a><span data-ttu-id="3dd1c-120">ログ プロバイダーの保存</span><span class="sxs-lookup"><span data-stu-id="3dd1c-120">Persisting the Log Provider</span></span>  
 <span data-ttu-id="3dd1c-121">通常、接続マネージャーに対して、カスタムの永続性を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-121">Ordinarily you do not have to implement custom persistence for a connection manager.</span></span> <span data-ttu-id="3dd1c-122">カスタムの永続性は、オブジェクトのプロパティで複合データ型が使用されている場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-122">Custom persistence is required only when the properties of an object use complex data types.</span></span> <span data-ttu-id="3dd1c-123">詳細については、「[Integration Services 用のカスタム オブジェクトの開発](../developing-custom-objects-for-integration-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-123">For more information, see [Developing Custom Objects for Integration Services](../developing-custom-objects-for-integration-services.md).</span></span>  
  
## <a name="logging-with-the-log-provider"></a><span data-ttu-id="3dd1c-124">ログ プロバイダーによるログ記録</span><span class="sxs-lookup"><span data-stu-id="3dd1c-124">Logging with the Log Provider</span></span>  
 <span data-ttu-id="3dd1c-125">すべてのログ プロバイダーがオーバーライドする必要のある実行時のメソッドには、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-125">There are three run-time methods that must be overridden by all log providers: <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3dd1c-126">単一のパッケージを検証および実行している間に、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッドと <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドは複数回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-126">During the validation and execution of a single package, the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods are called more than one time.</span></span> <span data-ttu-id="3dd1c-127">カスタム コードで次のログを開いたり閉じたりすることにより、以前のログ エントリが上書きされることがないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-127">Make sure that your custom code does not cause earlier log entries to be overwritten by the next opening and closing of the log.</span></span> <span data-ttu-id="3dd1c-128">テスト パッケージで検証イベントをログに記録することを選択した場合、最初にログに記録されるイベントは OnPreValidate です。最初にログに記録されているイベントが PackageStart である場合、最初の検証イベントが上書きされています。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-128">If you have selected to log validation events in your test package, the first logged event that you should see is OnPreValidate; if instead the first logged event that you see is PackageStart, the initial validation events have been overwritten.</span></span>  
  
### <a name="opening-the-log"></a><span data-ttu-id="3dd1c-129">ログを開く</span><span class="sxs-lookup"><span data-stu-id="3dd1c-129">Opening the Log</span></span>  
 <span data-ttu-id="3dd1c-130">ほとんどのログ プロバイダーは、ファイルやデータベースなどの外部データ ソースに接続し、パッケージの実行中に収集されるイベント情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-130">Most log providers connect to an external data source, such as a file or database, to store the event information that is collected during package execution.</span></span> <span data-ttu-id="3dd1c-131">ランタイム内の他のオブジェクトと同様に、外部データ ソースへの接続は、通常は接続マネージャー オブジェクトを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-131">As with any other object in the runtime, connecting to the external data source is typically accomplished by using connection manager objects.</span></span>  
  
 <span data-ttu-id="3dd1c-132">パッケージの実行の開始時に、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッドが呼び出されます。このメソッドをオーバーライドし、外部データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-132">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method is called at the start of package execution.Override this method to establish a connection to the external data source.</span></span>  
  
 <span data-ttu-id="3dd1c-133">次のコード例では、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッドが書き込むテキスト ファイルを開くログ プロバイダーを示します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-133">The following sample code shows a log provider that opens a text file for writing during <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>.</span></span> <span data-ttu-id="3dd1c-134">ここでは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> プロパティで指定されている接続マネージャーの <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> メソッドを呼び出すことによってファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-134">It opens the file by calling the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of the connection manager that was specified in the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property.</span></span>  
  
```csharp  
public override void OpenLog()  
{  
    if(!this.connections.Contains(this.ConfigString))  
        throw new Exception("The ConnectionManager " + this.ConfigString + " does not exist in the Connections collection.");  
  
    this.connectionManager = connections[ConfigString];  
    string filePath = this.connectionManager.AcquireConnection(null) as string;  
  
    if(filePath == null || filePath.Length == 0)  
        throw new Exception("The ConnectionManager " + this.ConfigString + " is not a valid FILE ConnectionManager");  
  
    //  Create a StreamWriter to append to.  
    sw = new StreamWriter(filePath,true);  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString());  
}  
```  
  
```vb  
Public Overrides  Sub OpenLog()  
    If Not Me.connections.Contains(Me.ConfigString) Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " does not exist in the Connections collection.")  
    End If  
  
    Me.connectionManager = connections(ConfigString)  
    Dim filePath As String =  Me.connectionManager.AcquireConnectionCType(as string, Nothing)  
  
    If filePath = Nothing Or filePath.Length = 0 Then  
        Throw New Exception("The ConnectionManager " + Me.ConfigString + " is not a valid FILE ConnectionManager")  
    End If  
  
    '  Create a StreamWriter to append to.  
    sw = New StreamWriter(filePath,True)  
  
    sw.WriteLine("Open log" + System.DateTime.Now.ToShortTimeString())  
End Sub  
```  
  
### <a name="writing-log-entries"></a><span data-ttu-id="3dd1c-135">ログ エントリの記述</span><span class="sxs-lookup"><span data-stu-id="3dd1c-135">Writing Log Entries</span></span>  
 <span data-ttu-id="3dd1c-136">パッケージ内のオブジェクトがいずれかのイベント インターフェイスで Fire\<event> メソッドを呼び出してイベントを発生させるたびに、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-136">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method is called every time that an object in the package raises an event by calling a Fire\<event> method on one of the event interfaces.</span></span> <span data-ttu-id="3dd1c-137">各イベントを発生させるときは、イベントのコンテキスト情報に加えて、通常は説明のメッセージが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-137">Each event is raised with information about its context and usually an explanatory message.</span></span> <span data-ttu-id="3dd1c-138">ただし、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドのすべての呼び出しに、すべてのメソッド パラメーターの情報が含まれているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-138">However, not every call to the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method includes information for every method parameter.</span></span> <span data-ttu-id="3dd1c-139">たとえば、名前が説明になっている一部の標準イベントは MessageText を提供しません。また DataCode と DataBytes は、省略可能な補足情報のためのものです。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-139">For example, some standard events whose names are self-explanatory do not provide MessageText, and DataCode and DataBytes are intended for optional supplemental information.</span></span>  
  
 <span data-ttu-id="3dd1c-140">次のコード例では、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッドを実装し、前のセクションで開かれたストリームにイベントを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-140">The following code example implements the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> method, and writes the events to the stream that was opened in the previous section.</span></span>  
  
```csharp  
public override void Log(string logEntryName, string computerName, string operatorName, string sourceName, string sourceID, string executionID, string messageText, DateTime startTime, DateTime endTime, int dataCode, byte[] dataBytes)  
{  
    sw.Write(logEntryName + ",");  
    sw.Write(computerName + ",");  
    sw.Write(operatorName + ",");  
    sw.Write(sourceName + ",");  
    sw.Write(sourceID + ",");  
    sw.Write(messageText + ",");  
    sw.Write(dataBytes + ",");  
    sw.WriteLine("");  
}  
```  
  
```vb  
Public Overrides  Sub Log(ByVal logEnTryName As String, ByVal computerName As String, ByVal operatorName As String, ByVal sourceName As String, ByVal sourceID As String, ByVal executionID As String, ByVal messageText As String, ByVal startTime As DateTime, ByVal endTime As DateTime, ByVal dataCode As Integer, ByVal dataBytes() As Byte)  
    sw.Write(logEnTryName + ",")  
    sw.Write(computerName + ",")  
    sw.Write(operatorName + ",")  
    sw.Write(sourceName + ",")  
    sw.Write(sourceID + ",")  
    sw.Write(messageText + ",")  
    sw.Write(dataBytes + ",")  
    sw.WriteLine("")  
End Sub  
```  
  
### <a name="closing-the-log"></a><span data-ttu-id="3dd1c-141">ログを閉じる</span><span class="sxs-lookup"><span data-stu-id="3dd1c-141">Closing the Log</span></span>  
 <span data-ttu-id="3dd1c-142">パッケージ内のすべてのオブジェクトが実行を完了するか、またはパッケージがエラーのために停止したとき、パッケージ実行の最後に <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-142">The <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method is called at the end of package execution, after all the objects in the package have completed execution, or, when the package stops because of errors.</span></span>  
  
 <span data-ttu-id="3dd1c-143">次のコード例では、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドで開かれたファイル ストリームを閉じる <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッドの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-143">The following code example demonstrates an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> method that closes the file stream that was opened during the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> method.</span></span>  
  
```csharp  
public override void CloseLog()  
{  
    if (sw != null)  
    {  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString());  
        sw.Close();  
    }  
}  
```  
  
```vb  
Public Overrides  Sub CloseLog()  
    If Not sw Is Nothing Then  
        sw.WriteLine("Close log" + System.DateTime.Now.ToShortTimeString())  
        sw.Close()  
    End If  
End Sub  
```  
  
<span data-ttu-id="3dd1c-144">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="3dd1c-144">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3dd1c-145">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-145">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3dd1c-146">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="3dd1c-146">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3dd1c-147">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="3dd1c-147">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd1c-148">参照</span><span class="sxs-lookup"><span data-stu-id="3dd1c-148">See Also</span></span>  
 <span data-ttu-id="3dd1c-149">[カスタム ログ プロバイダーの作成](creating-a-custom-log-provider.md) </span><span class="sxs-lookup"><span data-stu-id="3dd1c-149">[Creating a Custom Log Provider](creating-a-custom-log-provider.md) </span></span>  
 [<span data-ttu-id="3dd1c-150">カスタム ログ プロバイダー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="3dd1c-150">Developing a User Interface for a Custom Log Provider</span></span>](developing-a-user-interface-for-a-custom-log-provider.md)  
  
  
