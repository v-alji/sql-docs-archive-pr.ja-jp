---
title: スクリプト タスクによる Active Directory へのクエリの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Active Directory access
- SSIS Script task, Active Directory access
- Script task [Integration Services], examples
- Active Directory [Integration Services]
ms.assetid: a88fefbb-9ea2-4a86-b836-e71315bac68e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 624aa56289b9cab9174882b586a37e5d0de7ca9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632623"
---
# <a name="querying-the-active-directory-with-the-script-task"></a><span data-ttu-id="3aa9f-102">スクリプト タスクによる Active Directory へのクエリの実行</span><span class="sxs-lookup"><span data-stu-id="3aa9f-102">Querying the Active Directory with the Script Task</span></span>
  <span data-ttu-id="3aa9f-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージなどの企業データ処理アプリケーションでは、Active Directory に格納されている従業員の階級、役職、またはその他の特性に基づいて、個別にデータを処理する必要性が頻繁に生じます。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-103">Enterprise data processing applications, such as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages, often need to process data differently based on the rank, job title, or other characteristics of employees stored in Active Directory.</span></span> <span data-ttu-id="3aa9f-104">Active Directory は [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ディレクトリ サービスで、ユーザーに関するメタデータだけでなく、コンピューターやプリンターなどの他の組織資産に関するメタデータも集中して格納します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-104">Active Directory is a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows directory service that provides a centralized store of metadata, not only about users, but also about other organizational assets such as computers and printers.</span></span> <span data-ttu-id="3aa9f-105">Microsoft .NET Framework の `System.DirectoryServices` 名前空間では、Active Directory を使用して作業するためのクラスが用意されており、これを使用すると Active Directory が格納している情報に基づくデータ処理のワークフローを送信できます。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-105">The `System.DirectoryServices` namespace in the Microsoft .NET Framework provides classes for working with Active Directory, to help you direct data processing workflow based on the information that it stores.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aa9f-106">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="3aa9f-107">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="3aa9f-108">説明</span><span class="sxs-lookup"><span data-stu-id="3aa9f-108">Description</span></span>  
 <span data-ttu-id="3aa9f-109">次の例では、従業員の電子メール アドレスを格納する `email` 変数の値に基づき、従業員の名前、役職、および電話番号を Active Directory から取得します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-109">The following example retrieves an employee's name, title, and phone number from Active Directory based on the value of the `email` variable, which contains the e-mail address of the employee.</span></span> <span data-ttu-id="3aa9f-110">パッケージ内の優先順位制約は取得された情報を使用して、たとえば、優先度の低い電子メール メッセージを送信するか、または優先度の高いページを送信するかを従業員の役職に基づいて決定できます。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-110">Precedence constraints in the package can use the retrieved information to determine, for example, whether to send a low-priority e-mail message or a high-priority page, based on the job title of the employee.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="3aa9f-111">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="3aa9f-111">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="3aa9f-112">`email`、`name`、および `title` という 3 つの文字列変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-112">Create the three string variables `email`, `name`, and `title`.</span></span> <span data-ttu-id="3aa9f-113">`email` 変数の値に企業の有効な電子メール アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-113">Enter a valid corporate email address as the value of the `email` variable.</span></span>  
  
2.  <span data-ttu-id="3aa9f-114">[**スクリプトタスクエディター**] の [**スクリプト**] ページで、 `email` プロパティに変数を追加し `ReadOnlyVariables` ます。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-114">On the **Script** page of the **Script Task Editor**, add the `email` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="3aa9f-115">`name` および `title` 変数は、`ReadWriteVariables` プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-115">Add the `name` and `title` variables to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="3aa9f-116">このスクリプト プロジェクトでは、参照を `System.DirectoryServices` 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-116">In the script project, add a reference to the `System.DirectoryServices` namespace.</span></span>  
  
5.  <span data-ttu-id="3aa9f-117">。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-117">.</span></span> <span data-ttu-id="3aa9f-118">実際のコードでは、`Imports` ステートメントを使用し、`DirectoryServices` 名前空間をインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-118">In your code, use an `Imports` statement to import the `DirectoryServices` namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3aa9f-119">このスクリプトを正しく実行するには、組織のネットワーク上で Active Directory が使用され、この例で使用される従業員の情報が格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-119">To run this script successfully, your company must be using Active Directory on its network and storing the employee information that this example uses.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3aa9f-120">コード</span><span class="sxs-lookup"><span data-stu-id="3aa9f-120">Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim directory As DirectoryServices.DirectorySearcher  
    Dim result As DirectoryServices.SearchResult  
    Dim email As String  
  
    email = Dts.Variables("email").Value.ToString  
  
    Try  
        directory = New _  
            DirectoryServices.DirectorySearcher("(mail=" & email & ")")  
        result = directory.FindOne  
        Dts.Variables("name").Value = _  
            result.Properties("displayname").ToString  
        Dts.Variables("title").Value = _  
            result.Properties("title").ToString  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, _  
            "Script Task Example", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
```  
  
```csharp  
public void Main()  
{  
    //  
    DirectorySearcher directory;  
    SearchResult result;  
    string email;  
  
    email = (string)Dts.Variables["email"].Value;  
  
    try  
    {  
        directory = new DirectorySearcher("(mail=" + email + ")");  
        result = directory.FindOne();  
        Dts.Variables["name"].Value = result.Properties["displayname"].ToString();  
        Dts.Variables["title"].Value = result.Properties["title"].ToString();  
        Dts.TaskResult = (int)ScriptResults.Success;  
    }  
    catch (Exception ex)  
    {  
        Dts.Events.FireError(0, "Script Task Example", ex.Message + "\n" + ex.StackTrace, String.Empty, 0);  
        Dts.TaskResult = (int)ScriptResults.Failure;  
    }  
  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="3aa9f-121">外部リソース</span><span class="sxs-lookup"><span data-stu-id="3aa9f-121">External Resources</span></span>  
  
-   <span data-ttu-id="3aa9f-122">social.technet.microsoft.com の技術記事「[SSIS での Active Directory 情報の処理](https://go.microsoft.com/fwlink/?LinkId=199588)」</span><span class="sxs-lookup"><span data-stu-id="3aa9f-122">Technical article, [Processing Active Directory Information in SSIS](https://go.microsoft.com/fwlink/?LinkId=199588), on social.technet.microsoft.com</span></span>  
  
<span data-ttu-id="3aa9f-123">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="3aa9f-123">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="3aa9f-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="3aa9f-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="3aa9f-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="3aa9f-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="3aa9f-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
