---
title: スクリプト タスクによる ForEach ループの一覧の収集 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], Foreach loops
- Script task [Integration Services], examples
- SSIS Script task, Foreach loops
ms.assetid: 694f0462-d0c5-4191-b64e-821b1bdef055
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 039860da121efaa52115bb515b158ea10373e459
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713313"
---
# <a name="gathering-a-list-for-the-foreach-loop-with-the-script-task"></a><span data-ttu-id="cc002-102">スクリプト タスクによる ForEach ループの一覧の収集</span><span class="sxs-lookup"><span data-stu-id="cc002-102">Gathering a List for the ForEach Loop with the Script Task</span></span>
  <span data-ttu-id="cc002-103">Foreach from Variable 列挙子は、変数で渡された一覧の項目を列挙し、各項目に対して同じタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="cc002-103">The Foreach from Variable Enumerator enumerates over the items in a list that is passed to it in a variable and performs the same tasks on each item.</span></span> <span data-ttu-id="cc002-104">スクリプト タスクでカスタム コードを使用して、このための一覧を設定することができます。</span><span class="sxs-lookup"><span data-stu-id="cc002-104">You can use custom code in a Script task to populate a list for this purpose.</span></span> <span data-ttu-id="cc002-105">この列挙子の詳細については、「[Foreach ループ コンテナー](../control-flow/foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc002-105">For more information about the enumerator, see [Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc002-106">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="cc002-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="cc002-107">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc002-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc002-108">説明</span><span class="sxs-lookup"><span data-stu-id="cc002-108">Description</span></span>  
 <span data-ttu-id="cc002-109">次の例は、`System.IO` 名前空間のメソッドを使用して、ユーザーが変数で指定した日数より新しいまたは古い Excel ブックの一覧をコンピューターで収集します。</span><span class="sxs-lookup"><span data-stu-id="cc002-109">The following example uses methods from the `System.IO` namespace to gather a list of Excel workbooks on the computer that are either newer or older than a number of days specified by the user in a variable.</span></span> <span data-ttu-id="cc002-110">拡張子 .xls を持つファイルを探して C ドライブのディレクトリを再帰的に検索し、各ファイルの最終更新日を調べて、一覧に属するかどうかを判定します。</span><span class="sxs-lookup"><span data-stu-id="cc002-110">It searches directories on Drive C recursively for files that have the .xls extension and examines the date on which each file was last modified to determine whether the file belongs in the list.</span></span> <span data-ttu-id="cc002-111">該当するファイルを `ArrayList` に追加した後、その `ArrayList` を変数に保存して、後に Foreach ループ コンテナーで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cc002-111">It adds qualifying files to an `ArrayList` and saves the `ArrayList` to a variable for later use in a Foreach Loop container.</span></span> <span data-ttu-id="cc002-112">この Foreach ループ コンテナーは、Foreach from Variable 列挙子を使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="cc002-112">The Foreach Loop container is configured to use the Foreach from Variable enumerator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cc002-113">Foreach From Variable 列挙子で使用する変数は、`Object` 型であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="cc002-113">The variable that you use with the Foreach from Variable Enumerator must be of type `Object`.</span></span> <span data-ttu-id="cc002-114">変数に配置するオブジェクトは、`System.Collections.IEnumerable`、`System.Runtime.InteropServices.ComTypes.IEnumVARIANT`、`System.ComponentModel IListSource`、`Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost` のいずれかのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc002-114">The object that you place in the variable must implement one of the following interfaces: `System.Collections.IEnumerable`, `System.Runtime.InteropServices.ComTypes.IEnumVARIANT`, `System.ComponentModel IListSource`, or `Microsoft.SqlServer.Dts.Runtime.Wrapper.ForEachEnumeratorHost`.</span></span> <span data-ttu-id="cc002-115">`Array` または `ArrayList` が一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc002-115">An `Array` or `ArrayList` is commonly used.</span></span> <span data-ttu-id="cc002-116">`ArrayList` は、`Imports` 名前空間に対する参照と `System.Collections` ステートメントを必要とします。</span><span class="sxs-lookup"><span data-stu-id="cc002-116">The `ArrayList` requires a reference and an `Imports` statement for the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="cc002-117">このタスクは、`FileAge` パッケージ変数に対して正および負のさまざまな値を使用することによってテストできます。</span><span class="sxs-lookup"><span data-stu-id="cc002-117">You can experiment with this task by using different positive and negative values for the `FileAge` package variable.</span></span> <span data-ttu-id="cc002-118">たとえば、この 5 日間に作成されたファイルを検索するには 5 を入力し、3 日前よりも前に作成されたファイルを検索するには -3 を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc002-118">For example, you can enter 5 to search for files created in the last five days, or enter -3 to search for files that were created more than three days ago.</span></span> <span data-ttu-id="cc002-119">このタスクは、検索するフォルダーの数が多いドライブの場合、実行に 1 ～ 2 分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc002-119">This task may take a minute or two on a drive with many folders to search.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="cc002-120">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="cc002-120">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="cc002-121">`FileAge` という integer 型のパッケージ変数を作成し、正または負の整数値を入力します。</span><span class="sxs-lookup"><span data-stu-id="cc002-121">Create a package variable named `FileAge` of type integer and enter a positive or negative integer value.</span></span> <span data-ttu-id="cc002-122">値が正の場合は、指定した日数より新しいファイルが検索され、値が負の場合は、指定した日数より古いファイルが検索されます。</span><span class="sxs-lookup"><span data-stu-id="cc002-122">When the value is positive, the code searches for files newer than the specified number of days; when negative, for files older than the specified number of days.</span></span>  
  
2.  <span data-ttu-id="cc002-123">スクリプト タスクによって収集されたファイルの一覧を受け取るために、`FileList` という `Object` 型のパッケージ変数を作成します。この変数を後に Foreach from Variable 列挙子で使用します。</span><span class="sxs-lookup"><span data-stu-id="cc002-123">Create a package variable named `FileList` of type `Object` to receive the list of files gathered by the Script task for later use by the Foreach from Variable Enumerator.</span></span>  
  
3.  <span data-ttu-id="cc002-124">`FileAge` 変数をスクリプト タスクの `ReadOnlyVariables` プロパティに追加し、`FileList` 変数を `ReadWriteVariables` プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="cc002-124">Add the `FileAge` variable to the Script task's `ReadOnlyVariables` property, and add the `FileList` variable to the `ReadWriteVariables` property.</span></span>  
  
4.  <span data-ttu-id="cc002-125">コードで、 `System.Collections` との名前空間をインポートし `System.IO` ます。</span><span class="sxs-lookup"><span data-stu-id="cc002-125">In your code, import the `System.Collections` and the `System.IO` namespaces.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cc002-126">コード</span><span class="sxs-lookup"><span data-stu-id="cc002-126">Code</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.Collections  
Imports System.IO  
  
Public Class ScriptMain  
  
  Private Const FILE_AGE As Integer = -50  
  
  Private Const FILE_ROOT As String = "C:\"  
  Private Const FILE_FILTER As String = "*.xls"  
  
  Private isCheckForNewer As Boolean = True  
  Dim fileAgeLimit As Integer  
  Private listForEnumerator As ArrayList  
  
  Public Sub Main()  
  
    fileAgeLimit = DirectCast(Dts.Variables("FileAge").Value, Integer)  
  
    ' If value provided is positive, we want files NEWER THAN n days.  
    '  If negative, we want files OLDER THAN n days.  
    If fileAgeLimit < 0 Then  
      isCheckForNewer = False  
    End If  
    ' Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit)  
  
    listForEnumerator = New ArrayList  
  
    GetFilesInFolder(FILE_ROOT)  
  
    ' Return the list of files to the variable  
    '  for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: " & listForEnumerator.Count.ToString, "Results", Windows.Forms.MessageBoxButtons.OK, Windows.Forms.MessageBoxIcon.Information)  
    Dts.Variables("FileList").Value = listForEnumerator  
  
    Dts.TaskResult = ScriptResults.Success  
  
  End Sub  
  
  Private Sub GetFilesInFolder(ByVal folderPath As String)  
  
    Dim localFiles() As String  
    Dim localFile As String  
    Dim fileChangeDate As Date  
    Dim fileAge As TimeSpan  
    Dim fileAgeInDays As Integer  
    Dim childFolder As String  
  
    Try  
      localFiles = Directory.GetFiles(folderPath, FILE_FILTER)  
      For Each localFile In localFiles  
        fileChangeDate = File.GetLastWriteTime(localFile)  
        fileAge = DateTime.Now.Subtract(fileChangeDate)  
        fileAgeInDays = fileAge.Days  
        CheckAgeOfFile(localFile, fileAgeInDays)  
      Next  
  
      If Directory.GetDirectories(folderPath).Length > 0 Then  
        For Each childFolder In Directory.GetDirectories(folderPath)  
          GetFilesInFolder(childFolder)  
        Next  
      End If  
  
    Catch  
      ' Ignore exceptions on special folders such as System Volume Information.  
    End Try  
  
  End Sub  
  
  Private Sub CheckAgeOfFile(ByVal localFile As String, ByVal fileAgeInDays As Integer)  
  
    If isCheckForNewer Then  
      If fileAgeInDays <= fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    Else  
      If fileAgeInDays > fileAgeLimit Then  
        listForEnumerator.Add(localFile)  
      End If  
    End If  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Math;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Collections;  
using System.IO;  
  
public partial class ScriptMain : Microsoft.SqlServer.Dts.Tasks.ScriptTask.VSTARTScriptObjectModelBase  
    {  
  
        private const int FILE_AGE = -50;  
  
        private const string FILE_ROOT = "C:\\";  
        private const string FILE_FILTER = "*.xls";  
  
        private bool isCheckForNewer = true;  
        int fileAgeLimit;  
        private ArrayList listForEnumerator;  
  
        public void Main()  
  {  
  
    fileAgeLimit = (int)(Dts.Variables["FileAge"].Value);  
  
    // If value provided is positive, we want files NEWER THAN n days.  
    // If negative, we want files OLDER THAN n days.  
    if (fileAgeLimit<0)  
    {  
      isCheckForNewer = false;  
    }  
    // Extract number of days as positive integer.  
    fileAgeLimit = Math.Abs(fileAgeLimit);  
  
    ArrayList listForEnumerator = new ArrayList();  
  
    GetFilesInFolder(FILE_ROOT);  
  
    // Return the list of files to the variable  
    // for later use by the Foreach from Variable enumerator.  
    System.Windows.Forms.MessageBox.Show("Matching files: "+ listForEnumerator.Count, "Results",   
MessageBoxButtons.OK, MessageBoxIcon.Information);  
    Dts.Variables["FileList"].Value = listForEnumerator;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  
  }  
  
        private void GetFilesInFolder(string folderPath)  
        {  
  
            string[] localFiles;  
            DateTime fileChangeDate;  
            TimeSpan fileAge;  
            int fileAgeInDays;  
  
            try  
            {  
                localFiles = Directory.GetFiles(folderPath, FILE_FILTER);  
                foreach (string localFile in localFiles)  
                {  
                    fileChangeDate = File.GetLastWriteTime(localFile);  
                    fileAge = DateTime.Now.Subtract(fileChangeDate);  
                    fileAgeInDays = fileAge.Days;  
                    CheckAgeOfFile(localFile, fileAgeInDays);  
                }  
  
                if (Directory.GetDirectories(folderPath).Length > 0)  
                {  
                    foreach (string childFolder in Directory.GetDirectories(folderPath))  
                    {  
                        GetFilesInFolder(childFolder);  
                    }  
                }  
  
            }  
            catch  
            {  
                // Ignore exceptions on special folders, such as System Volume Information.  
            }  
  
        }  
  
        private void CheckAgeOfFile(string localFile, int fileAgeInDays)  
        {  
  
            if (isCheckForNewer)  
            {  
                if (fileAgeInDays <= fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
            else  
            {  
                if (fileAgeInDays > fileAgeLimit)  
                {  
                    listForEnumerator.Add(localFile);  
                }  
            }  
  
        }  
  
    }  
```  
  
<span data-ttu-id="cc002-127">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="cc002-127">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="cc002-128">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc002-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="cc002-129">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="cc002-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="cc002-130">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="cc002-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc002-131">参照</span><span class="sxs-lookup"><span data-stu-id="cc002-131">See Also</span></span>  
 <span data-ttu-id="cc002-132">[Foreach ループコンテナー](../control-flow/foreach-loop-container.md) </span><span class="sxs-lookup"><span data-stu-id="cc002-132">[Foreach Loop Container](../control-flow/foreach-loop-container.md) </span></span>  
 [<span data-ttu-id="cc002-133">Foreach ループコンテナーの構成</span><span class="sxs-lookup"><span data-stu-id="cc002-133">Configure a Foreach Loop Container</span></span>](../configure-a-foreach-loop-container.md)  
  
  
