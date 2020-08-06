---
title: Windows アプリケーションでの URL アクセスの使用 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Windows applications [Reporting Services]
- Web Browser controls [Reporting Services]
- Windows Forms [Reporting Services]
- browser controls [Reporting Services]
- URL access [Reporting Services], Windows applications
ms.assetid: a4b222e5-0cbd-409c-92c4-046a674db8ac
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8f8b901481b1d6fcc3cdd8626b43cd3a69174c1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719730"
---
# <a name="using-url-access-in-a-windows-application"></a><span data-ttu-id="cf0f9-102">Windows アプリケーションでの URL アクセスの使用</span><span class="sxs-lookup"><span data-stu-id="cf0f9-102">Using URL Access in a Windows Application</span></span>
  <span data-ttu-id="cf0f9-103">レポート サーバーへの URL アクセスは Web 環境用に最適化されていますが、URL アクセスを使用して [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートを [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーションに埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-103">Although URL access to a report server is optimized for a Web environment, you can also use URL access to embed [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] reports into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows application.</span></span> <span data-ttu-id="cf0f9-104">ただし、Windows フォームに関連する URL アクセスでは、Web ブラウザー テクノロジを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-104">However, URL access that involves Windows Forms still requires that you use Web browser technology.</span></span> <span data-ttu-id="cf0f9-105">URL アクセスと Windows フォームでは、次の統合シナリオを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-105">You can use the following integration scenarios with URL access and Windows Forms:</span></span>  
  
-   <span data-ttu-id="cf0f9-106">プログラムで Web ブラウザーを起動し、Windows フォーム アプリケーションからレポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-106">Display a report from a Windows Form application by starting a Web browser programmatically.</span></span>  
  
-   <span data-ttu-id="cf0f9-107">Windows フォームで <xref:System.Windows.Forms.WebBrowser> コントロールを使用し、レポートを表示します。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-107">Use the <xref:System.Windows.Forms.WebBrowser> control on a Windows Form to display a report.</span></span>  
  
## <a name="starting-internet-explorer-from-a-windows-form"></a><span data-ttu-id="cf0f9-108">Windows フォームからの Internet Explorer の起動</span><span class="sxs-lookup"><span data-stu-id="cf0f9-108">Starting Internet Explorer from a Windows Form</span></span>  
 <span data-ttu-id="cf0f9-109"><xref:System.Diagnostics.Process> クラスを使用して、コンピューターで実行されているプロセスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-109">You can use the <xref:System.Diagnostics.Process> class to access a process that is running on a computer.</span></span> <span data-ttu-id="cf0f9-110">クラスは、 <xref:System.Diagnostics.Process> アプリケーションを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 起動、停止、制御、および監視するための便利な構成要素です。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-110">The <xref:System.Diagnostics.Process> class is a useful [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] construct for starting, stopping, controlling, and monitoring applications.</span></span> <span data-ttu-id="cf0f9-111">レポート サーバー データベースの特定のレポートを表示するには、レポートへの URL を渡して **IExplore** プロセスを起動できます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-111">To view a specific report in your report server database, you can start the **IExplore** process, passing in the URL to the report.</span></span> <span data-ttu-id="cf0f9-112">次のコード例を使用すると、ユーザーが Windows フォームのボタンをクリックしたときに [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer が起動し、特定のレポート URL を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-112">The following code example can be used to start [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Explorer and pass a specific report URL when the user clicks a button on a Windows Form.</span></span>  
  
```vb  
Private Sub viewReportButton_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles viewReportButton.Click  
   ' Build the URL access string based on values supplied by a user  
   Dim url As String = serverUrlTextBox.Text + "?" & reportPathTextBox.Text & _  
   "&rs:Command=Render" & "&rs:Format=HTML4.0"  
  
   ' If the user does not select the toolbar check box,  
   ' turn the toolbar off in the HTML Viewer  
   If toolbarCheckBox.Checked = False Then  
      url += "&rc:Toolbar=False"  
   End If  
   ' load report in the Web browser  
   Try  
      System.Diagnostics.Process.Start("IExplore", url)  
   Catch  
      MessageBox.Show("The system could not start the specified report using Internet Explorer.", _  
      "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error)  
   End Try  
End Sub 'viewReportButton_Click  
```  
  
```csharp  
// Sample click event for a Button control on a Windows Form  
private void viewReportButton_Click(object sender, System.EventArgs e)  
{  
   // Build the URL access string based on values supplied by a user  
   string url = serverUrlTextBox.Text + "?" + reportPathTextBox.Text +  
      "&rs:Command=Render" + "&rs:Format=HTML4.0";  
  
   // If the user does not check the toolbar check box,  
   // turn the toolbar off in the HTML Viewer  
   if (toolbarCheckBox.Checked == false)  
      url += "&rc:Toolbar=False";  
  
   // load report in the Web browser  
   try  
   {  
      System.Diagnostics.Process.Start("IExplore", url);  
   }  
  
   catch (Exception)  
   {  
      MessageBox.Show(  
         "The system could not open the specified report using Internet Explorer.",   
         "An error has occurred", MessageBoxButtons.OK, MessageBoxIcon.Error);  
   }  
}  
```  
  
## <a name="embedding-a-browser-control-on-a-windows-form"></a><span data-ttu-id="cf0f9-113">Windows フォームへのブラウザー コントロールの埋め込み</span><span class="sxs-lookup"><span data-stu-id="cf0f9-113">Embedding a Browser Control on a Windows Form</span></span>  
 <span data-ttu-id="cf0f9-114">外部 Web ブラウザーでレポートを表示したくない場合は、<xref:System.Windows.Forms.WebBrowser> コントロールを使用して、Windows フォームの一部としてシームレスに Web ブラウザーを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-114">If you do not want to view your report in an external Web browser, you can embed a Web browser seamlessly as part of your Windows Form using the <xref:System.Windows.Forms.WebBrowser> control.</span></span>  
  
###### <a name="to-add-the-webbrowser-control-to-your-windows-form"></a><span data-ttu-id="cf0f9-115">Windows フォームに WebBrowser コントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="cf0f9-115">To add the WebBrowser control to your Windows Form</span></span>  
  
1.  <span data-ttu-id="cf0f9-116">またはのいずれかで、新しい Windows アプリケーションを作成 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] します。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-116">Create a new Windows application in either [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] or [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
2.  <span data-ttu-id="cf0f9-117">**[ツールボックス]** ダイアログ ボックスで <xref:System.Windows.Forms.WebBrowser> コントロールを探します。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-117">Locate the <xref:System.Windows.Forms.WebBrowser> control in the **Toolbox** Dialog Box.</span></span>  
  
     <span data-ttu-id="cf0f9-118">**ツールボックス**が表示されていない場合は、**[表示]** メニュー項目をクリックして **[ツールボックス]** を選択することでアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-118">If the **Toolbox** is not visible you can access it by clicking the **View** menu item and selecting **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="cf0f9-119"><xref:System.Windows.Forms.WebBrowser> コントロールを Windows フォームのデザイン画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-119">Drag the <xref:System.Windows.Forms.WebBrowser>control onto the design surface of your Windows Form.</span></span>  
  
     <span data-ttu-id="cf0f9-120">webBrowser1 という <xref:System.Windows.Forms.WebBrowser> コントロールがフォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-120">The <xref:System.Windows.Forms.WebBrowser>control named webBrowser1 is added to the Form</span></span>  
  
 <span data-ttu-id="cf0f9-121"><xref:System.Windows.Forms.WebBrowser> コントロールを URL に指定するには、その **Navigate** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-121">You direct the <xref:System.Windows.Forms.WebBrowser> control to a URL by calling its **Navigate** method.</span></span> <span data-ttu-id="cf0f9-122">次の例に示すように、実行時に特定の URL アクセス文字列を <xref:System.Windows.Forms.WebBrowser> コントロールに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cf0f9-122">You can assign a specific URL access string to your <xref:System.Windows.Forms.WebBrowser> control at run time as shown in the following example.</span></span>  
  
```vb  
Dim url As String = "http://localhost/reportserver?/" & _  
                    "AdventureWorks2012 Sample Reports/" & _  
                    "Company Sales&rs:Command=Render"  
WebBrowser1.Navigate(url)  
```  
  
```csharp  
string url = "http://localhost/reportserver?/" +  
             "AdventureWorks2012 Sample Reports/" +  
             "Company Sales&rs:Command=Render";  
webBrowser1.Navigate(url);  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf0f9-123">参照</span><span class="sxs-lookup"><span data-stu-id="cf0f9-123">See Also</span></span>  
 <span data-ttu-id="cf0f9-124">[アプリケーションへの Reporting Services の統合](../application-integration/integrating-reporting-services-into-applications.md) </span><span class="sxs-lookup"><span data-stu-id="cf0f9-124">[Integrating Reporting Services into Applications](../application-integration/integrating-reporting-services-into-applications.md) </span></span>  
 <span data-ttu-id="cf0f9-125">[URL アクセスを使用した Reporting Services の統合](integrating-reporting-services-using-url-access.md) </span><span class="sxs-lookup"><span data-stu-id="cf0f9-125">[Integrating Reporting Services Using URL Access](integrating-reporting-services-using-url-access.md) </span></span>  
 <span data-ttu-id="cf0f9-126">[SOAP を使用した Reporting Services の統合](integrating-reporting-services-using-soap.md) </span><span class="sxs-lookup"><span data-stu-id="cf0f9-126">[Integrating Reporting Services Using SOAP](integrating-reporting-services-using-soap.md) </span></span>  
 <span data-ttu-id="cf0f9-127">[ReportViewer コントロールを使用した Reporting Services の統合](integrating-reporting-services-using-reportviewer-controls.md) </span><span class="sxs-lookup"><span data-stu-id="cf0f9-127">[Integrating Reporting Services Using the ReportViewer Controls](integrating-reporting-services-using-reportviewer-controls.md) </span></span>  
 [<span data-ttu-id="cf0f9-128">URL アクセス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="cf0f9-128">URL Access &#40;SSRS&#41;</span></span>](../url-access-ssrs.md)  
  
  
