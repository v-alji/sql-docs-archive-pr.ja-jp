---
title: カスタム接続マネージャー用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], developing user interface
- custom user interface [Integration Services], custom connection manager
ms.assetid: 908bf2ac-fc84-4af8-a869-1cb43573d2df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc0e9f2a76f3d97c925c44219683ca6cd655e43f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640158"
---
# <a name="developing-a-user-interface-for-a-custom-connection-manager"></a><span data-ttu-id="4d582-102">カスタム接続マネージャー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="4d582-102">Developing a User Interface for a Custom Connection Manager</span></span>
  <span data-ttu-id="4d582-103">基本クラスのプロパティとメソッドをオーバーライドしてカスタム機能を提供したら、接続マネージャー用のカスタム ユーザー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d582-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your connection manager.</span></span> <span data-ttu-id="4d582-104">カスタム ユーザー インターフェイスを作成しない場合、ユーザーは [プロパティ] ウィンドウを使用して接続マネージャーを構成することしかできません。</span><span class="sxs-lookup"><span data-stu-id="4d582-104">If you do not create a custom user interface, users can configure your connection manager only by using the Properties window.</span></span>  
  
 <span data-ttu-id="4d582-105">1 つのカスタム ユーザー インターフェイスのプロジェクトまたはアセンブリには、通常 2 つのクラスがあります。<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> を実装するクラスと、このクラスによって表示される、ユーザーから情報を収集するための Windows フォームです。</span><span class="sxs-lookup"><span data-stu-id="4d582-105">In a custom user interface project or assembly, you normally have two classes-a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>, and the Windows form that it displays to gather information from the user.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4d582-106">「[カスタム接続マネージャーのコーディング](../building-deploying-and-debugging-custom-objects.md)」で説明されているようにカスタム ユーザー インターフェイスに署名してビルドし、グローバル アセンブリ キャッシュにインストールしたら、このクラスの完全修飾名を <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> プロパティで忘れずに指定してください。</span><span class="sxs-lookup"><span data-stu-id="4d582-106">After signing and building your custom user interface and installing it in the global assembly cache as described in [Coding a Custom Connection Manager](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d582-107">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="4d582-107">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="4d582-108">そのため、これらのサンプルは組み込みのタスクおよびコンポーネントではテストできません。</span><span class="sxs-lookup"><span data-stu-id="4d582-108">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="coding-the-user-interface-class"></a><span data-ttu-id="4d582-109">ユーザー インターフェイス クラスのコーディング</span><span class="sxs-lookup"><span data-stu-id="4d582-109">Coding the User Interface Class</span></span>  
 <span data-ttu-id="4d582-110"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> インターフェイスにはメソッドが 4 つあります。つまり、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A>、および <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> です。</span><span class="sxs-lookup"><span data-stu-id="4d582-110">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface has four methods: <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A>.</span></span> <span data-ttu-id="4d582-111">この後の各セクションで、これらの 4 つのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4d582-111">The following sections describe these four methods.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d582-112">ユーザーが接続マネージャーのインスタンスを削除したときにクリーンアップを実行する必要がない場合、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> メソッドのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4d582-112">You may not need to write any code for the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Delete%2A> method if no cleanup is required when the user deletes an instance of the connection manager.</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="4d582-113">ユーザー インターフェイスの初期化</span><span class="sxs-lookup"><span data-stu-id="4d582-113">Initializing the User Interface</span></span>  
 <span data-ttu-id="4d582-114"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> メソッドで、デザイナーは設定対象の接続マネージャーへの参照を提供し、ユーザー インターフェイス クラスで接続マネージャーのプロパティを変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4d582-114">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method, the designer provides a reference to the connection manager that is being configured so that the user interface class can modify the connection manager's properties.</span></span> <span data-ttu-id="4d582-115">次のコードに示すとおり、作成するコードで接続マネージャーへの参照をキャッシュして、後で使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d582-115">As shown in the following code, your code needs to cache the reference to the connection managerfor later use.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As Microsoft.SqlServer.Dts.Runtime.ConnectionManager, ByVal serviceProvider As System.IServiceProvider) Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize  
  
    _connectionManager = connectionManager  
    _serviceProvider = serviceProvider  
  
  End Sub  
```  
  
```csharp  
public void Initialize(Microsoft.SqlServer.Dts.Runtime.ConnectionManager connectionManager, System.IServiceProvider serviceProvider)  
{  
  
  _connectionManager = connectionManager;  
  _serviceProvider = serviceProvider;  
  
}  
```  
  
### <a name="creating-a-new-instance-of-the-user-interface"></a><span data-ttu-id="4d582-116">ユーザー インターフェイスの新しいインスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="4d582-116">Creating a New Instance of the User Interface</span></span>  
 <span data-ttu-id="4d582-117"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> メソッドはコンストラクターではありません。このメソッドは、ユーザーが接続マネージャーの新しいインスタンスを作成したときに、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> メソッドの後に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4d582-117">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, which is not a constructor, is called after the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Initialize%2A> method when the user creates a new instance of the connection manager.</span></span> <span data-ttu-id="4d582-118"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> メソッドでは、ユーザーが既存の接続マネージャーをコピーし、貼り付けていない限り、通常は編集用のフォームを表示します。</span><span class="sxs-lookup"><span data-stu-id="4d582-118">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> method, you usually want to display the form for editing, unless the user has copied and pasted an existing connection manager.</span></span> <span data-ttu-id="4d582-119">次のコードは、このメソッドを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4d582-119">The following code shows an implementation of this method.</span></span>  
  
```vb  
Public Function [New](ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArgs As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New  
  
  Dim clipboardService As IDtsClipboardService  
  
  clipboardService = _  
    DirectCast(_serviceProvider.GetService(GetType(IDtsClipboardService)), IDtsClipboardService)  
  If Not clipboardService Is Nothing Then  
    ' If the connection manager has been copied and pasted, take no action.  
    If clipboardService.IsPasteActive Then  
      Return True  
    End If  
  End If  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool New(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArgs)  
  {  
    IDtsClipboardService clipboardService;  
  
    clipboardService = (IDtsClipboardService)_serviceProvider.GetService(typeof(IDtsClipboardService));  
    if (clipboardService != null)  
    // If connection manager has been copied and pasted, take no action.  
    {  
      if (clipboardService.IsPasteActive)  
      {  
        return true;  
      }  
    }  
  
    return EditSqlConnection(parentWindow);  
  }  
```  
  
### <a name="editing-the-connection-manager"></a><span data-ttu-id="4d582-120">接続マネージャーの編集</span><span class="sxs-lookup"><span data-stu-id="4d582-120">Editing the Connection Manager</span></span>  
 <span data-ttu-id="4d582-121">編集用のフォームは <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> メソッドと <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> メソッドの両方から呼び出されるため、ヘルパー関数を使用して、フォームを表示するコードをカプセル化すると便利です。</span><span class="sxs-lookup"><span data-stu-id="4d582-121">Because the form for editing is called from both the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.New%2A> and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> methods, it is convenient to use a helper function to encapsulate the code that displays the form.</span></span> <span data-ttu-id="4d582-122">次のコードは、このヘルパー関数を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4d582-122">The following code shows an implementation of this helper function.</span></span>  
  
```vb  
Private Function EditSqlConnection(ByVal parentWindow As IWin32Window) As Boolean  
  
  Dim sqlCMUIForm As New SqlConnMgrUIFormVB  
  
  sqlCMUIForm.Initialize(_connectionManager, _serviceProvider)  
  If sqlCMUIForm.ShowDialog(parentWindow) = DialogResult.OK Then  
    Return True  
  Else  
    Return False  
  End If  
  
End Function  
```  
  
```csharp  
private bool EditSqlConnection(IWin32Window parentWindow)  
 {  
  
   SqlConnMgrUIFormCS sqlCMUIForm = new SqlConnMgrUIFormCS();  
  
   sqlCMUIForm.Initialize(_connectionManager, _serviceProvider);  
   if (sqlCMUIForm.ShowDialog(parentWindow) == DialogResult.OK)  
   {  
     return true;  
   }  
   else  
   {  
     return false;  
   }  
  
 }  
```  
  
 <span data-ttu-id="4d582-123"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> メソッドでは、編集用のフォームを表示するだけです。</span><span class="sxs-lookup"><span data-stu-id="4d582-123">In the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method, you simply have to display the form for editing.</span></span> <span data-ttu-id="4d582-124">次のコードは、ヘルパー関数を使用してフォームのコードをカプセル化する <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> メソッドを実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4d582-124">The following code shows an implementation of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit%2A> method that uses a helper function to encapsulate the code for the form.</span></span>  
  
```vb  
Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal connections As Microsoft.SqlServer.Dts.Runtime.Connections, ByVal connectionUIArg As Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs) As Boolean Implements Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI.Edit  
  
  Return EditSqlConnection(parentWindow)  
  
End Function  
```  
  
```csharp  
public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Microsoft.SqlServer.Dts.Runtime.Connections connections, Microsoft.SqlServer.Dts.Runtime.Design.ConnectionManagerUIArgs connectionUIArg)  
{  
  
  return EditSqlConnection(parentWindow);  
  
}  
```  
  
## <a name="coding-the-user-interface-form"></a><span data-ttu-id="4d582-125">ユーザー インターフェイス フォームのコーディング</span><span class="sxs-lookup"><span data-stu-id="4d582-125">Coding the User Interface Form</span></span>  
 <span data-ttu-id="4d582-126"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> インターフェイスのメソッドを実装するユーザー インターフェイス クラスを作成したら、ユーザーが接続マネージャーのプロパティを変更できる Windows フォームを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d582-126">After creating the user interface class that implements the methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface, you must create a Windows form where the user can configure the properties of your connection manager.</span></span>  
  
### <a name="initializing-the-user-interface-form"></a><span data-ttu-id="4d582-127">ユーザー インターフェイス フォームの初期化</span><span class="sxs-lookup"><span data-stu-id="4d582-127">Initializing the User Interface Form</span></span>  
 <span data-ttu-id="4d582-128">編集用のカスタム フォームを表示するときは、編集対象の接続マネージャーへの参照を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4d582-128">When you display your custom form for editing, you can pass a reference to the connection manager that is being edited.</span></span> <span data-ttu-id="4d582-129">この参照を渡すには、フォーム クラスのカスタム コンストラクターを使用するか、以下に示すような独自の `Initialize` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="4d582-129">You can pass this reference either by using a custom constructor for the form class, or by creating your own `Initialize` method as shown here.</span></span>  
  
```vb  
Public Sub Initialize(ByVal connectionManager As ConnectionManager, ByVal serviceProvider As IServiceProvider)  
  
  _connectionManager = connectionManager  
  _serviceProvider = serviceProvider  
  ConfigureControlsFromConnectionManager()  
  EnableControls()  
  
End Sub  
```  
  
```csharp  
public void Initialize(ConnectionManager connectionManager, IServiceProvider serviceProvider)  
 {  
  
   _connectionManager = connectionManager;  
   _serviceProvider = serviceProvider;  
   ConfigureControlsFromConnectionManager();  
   EnableControls();  
  
 }  
```  
  
### <a name="setting-properties-on-the-user-interface-form"></a><span data-ttu-id="4d582-130">ユーザー インターフェイス フォームでのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="4d582-130">Setting Properties on the User Interface Form</span></span>  
 <span data-ttu-id="4d582-131">最後に、フォーム クラスには、フォームを最初に読み込んだときに、接続マネージャーのプロパティの既存の値や既定の値を使用してフォーム上のコントロールを設定するヘルパー関数が必要です。</span><span class="sxs-lookup"><span data-stu-id="4d582-131">Finally, your form class needs a helper function that populates the controls on the form when it is first loaded with the existing or the default values of the properties of the connection manager.</span></span> <span data-ttu-id="4d582-132">またフォーム クラスには、ユーザーが [OK] をクリックしてフォームを閉じたときに、プロパティの値をユーザーによって入力された値に設定する、同じような関数も必要です。</span><span class="sxs-lookup"><span data-stu-id="4d582-132">Your form class also needs a similar function that sets the values of the properties to the values entered by the user when the user clicks OK and closes the form.</span></span>  
  
```vb  
Private Const CONNECTIONNAME_BASE As String = "SqlConnectionManager"  
  
Private Sub ConfigureControlsFromConnectionManager()  
  
  Dim tempName As String  
  Dim tempServerName As String  
  Dim tempDatabaseName As String  
  
  With _connectionManager  
  
    tempName = .Properties("Name").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempName) Then  
      _connectionName = tempName  
    Else  
      _connectionName = CONNECTIONNAME_BASE  
    End If  
  
    tempServerName = .Properties("ServerName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempServerName) Then  
      _serverName = tempServerName  
      txtServerName.Text = _serverName  
    End If  
  
    tempDatabaseName = .Properties("DatabaseName").GetValue(_connectionManager).ToString  
    If Not String.IsNullOrEmpty(tempDatabaseName) Then  
      _databaseName = tempDatabaseName  
      txtDatabaseName.Text = _databaseName  
    End If  
  
  End With  
  
End Sub  
  
Private Sub ConfigureConnectionManagerFromControls()  
  
  With _connectionManager  
    .Properties("Name").SetValue(_connectionManager, _connectionName)  
    .Properties("ServerName").SetValue(_connectionManager, _serverName)  
    .Properties("DatabaseName").SetValue(_connectionManager, _databaseName)  
  End With  
  
End Sub  
```  
  
```csharp  
private const string CONNECTIONNAME_BASE = "SqlConnectionManager";  
  
private void ConfigureControlsFromConnectionManager()  
 {  
  
   string tempName;  
   string tempServerName;  
   string tempDatabaseName;  
  
   {  
     tempName = _connectionManager.Properties["Name"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempName))  
     {  
       _connectionName = tempName;  
     }  
     else  
     {  
       _connectionName = CONNECTIONNAME_BASE;  
     }  
  
     tempServerName = _connectionManager.Properties["ServerName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempServerName))  
     {  
       _serverName = tempServerName;  
       txtServerName.Text = _serverName;  
     }  
  
     tempDatabaseName = _connectionManager.Properties["DatabaseName"].GetValue(_connectionManager).ToString();  
     if (!String.IsNullOrEmpty(tempDatabaseName))  
     {  
       _databaseName = tempDatabaseName;  
       txtDatabaseName.Text = _databaseName;  
     }  
  
   }  
  
 }  
  
 private void ConfigureConnectionManagerFromControls()  
 {  
  
   {  
     _connectionManager.Properties["Name"].SetValue(_connectionManager, _connectionName);  
     _connectionManager.Properties["ServerName"].SetValue(_connectionManager, _serverName);  
     _connectionManager.Properties["DatabaseName"].SetValue(_connectionManager, _databaseName);  
   }  
  
 }  
```  
  
<span data-ttu-id="4d582-133">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="4d582-133">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="4d582-134">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d582-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="4d582-135">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="4d582-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="4d582-136">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="4d582-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d582-137">参照</span><span class="sxs-lookup"><span data-stu-id="4d582-137">See Also</span></span>  
 <span data-ttu-id="4d582-138">[カスタム接続マネージャーの作成](creating-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4d582-138">[Creating a Custom Connection Manager](creating-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="4d582-139">カスタム接続マネージャーのコーディング</span><span class="sxs-lookup"><span data-stu-id="4d582-139">Coding a Custom Connection Manager</span></span>](coding-a-custom-connection-manager.md)  
  
  
