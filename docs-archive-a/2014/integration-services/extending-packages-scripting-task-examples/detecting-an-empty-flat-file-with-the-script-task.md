---
title: スクリプト タスクによる空のフラット ファイルの検出 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- flat files
- Script task [Integration Services], empty flat files
- SSIS Script task, empty flat files
- Script task [Integration Services], examples
ms.assetid: 1b4defb8-886a-483d-8056-d1b91d37bc90
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 379b11bd18752ad648fc5f24d11d9ed5bfb63e14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641735"
---
# <a name="detecting-an-empty-flat-file-with-the-script-task"></a><span data-ttu-id="481d9-102">スクリプト タスクによる空のフラット ファイルの検出</span><span class="sxs-lookup"><span data-stu-id="481d9-102">Detecting an Empty Flat File with the Script Task</span></span>
  <span data-ttu-id="481d9-103">フラット ファイル ソースでは、フラット ファイルを処理する前にデータ行が含まれるかどうかを判定しません。</span><span class="sxs-lookup"><span data-stu-id="481d9-103">The Flat File source does not determine whether a flat file contains rows of data before attempting to process it.</span></span> <span data-ttu-id="481d9-104">データ行を含まないファイルをスキップすることにより、パッケージの効率、特に多数のフラット ファイルを繰り返し処理するパッケージの効率を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="481d9-104">You may want to improve the efficiency of a package, especially of a package that iterates over numerous flat files, by skipping files that do not contain any rows of data.</span></span> <span data-ttu-id="481d9-105">スクリプト タスクによって、パッケージがデータ フローの処理を開始する前に空のフラット ファイルを確認できます。</span><span class="sxs-lookup"><span data-stu-id="481d9-105">The Script task can look for an empty flat file before the package begins to process the data flow.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="481d9-106">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="481d9-106">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="481d9-107">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="481d9-107">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
## <a name="description"></a><span data-ttu-id="481d9-108">説明</span><span class="sxs-lookup"><span data-stu-id="481d9-108">Description</span></span>  
 <span data-ttu-id="481d9-109">次の例では、`System.IO` 名前空間のメソッドを使用して、フラット ファイル接続マネージャーで指定されたフラット ファイルをテストし、ファイルが空かどうか、または列ヘッダーなどの必要な非データ行や空の行だけが含まれるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="481d9-109">The following example uses methods from the `System.IO` namespace to test the flat file specified in a Flat File connection manager to determine whether the file is empty, or whether it contains only expected non-data rows such as column headers or an empty line.</span></span> <span data-ttu-id="481d9-110">このスクリプトは最初にファイルのサイズをチェックします。サイズがゼロ バイトの場合、ファイルは空です。</span><span class="sxs-lookup"><span data-stu-id="481d9-110">The script checks the size of the file first; if the size is zero bytes, the file is empty.</span></span> <span data-ttu-id="481d9-111">ファイル サイズがゼロより大きい場合、行がなくなるまで、または必要な非データ行の数を超えるまでファイルから行を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="481d9-111">If the file size is greater than zero, the script reads lines from the file until there are no more lines, or until the number of lines exceeds the expected number of non-data rows.</span></span> <span data-ttu-id="481d9-112">ファイル内の行数が必要な非データ行の数以下の場合、そのファイルは空と見なされます。</span><span class="sxs-lookup"><span data-stu-id="481d9-112">If the number of lines in the file is less than or equal to the expected number of non-data rows, then the file is considered empty.</span></span> <span data-ttu-id="481d9-113">結果はユーザー変数内のブール値として返されます。この値は、パッケージの制御フローでの分岐に使用できます。</span><span class="sxs-lookup"><span data-stu-id="481d9-113">The result is returned as a Boolean value in a user variable, the value of which can be used for branching in the package's control flow.</span></span> <span data-ttu-id="481d9-114">また、このメソッドは、 `FireInformation` **Output** [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) の [出力] ウィンドウに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="481d9-114">The `FireInformation` method also displays the result in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="481d9-115">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="481d9-115">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="481d9-116">という名前のフラットファイル接続マネージャーを作成して構成し `EmptyFlatFileTest` ます。</span><span class="sxs-lookup"><span data-stu-id="481d9-116">Create and configure a flat file connection manager named `EmptyFlatFileTest`.</span></span>  
  
2.  <span data-ttu-id="481d9-117">`FFNonDataRows` という名前の整数変数を作成し、その値をフラット ファイルで必要な、非データ行の数に設定します。</span><span class="sxs-lookup"><span data-stu-id="481d9-117">Create an integer variable named `FFNonDataRows` and set its value to the number of non-data rows expected in the flat file.</span></span>  
  
3.  <span data-ttu-id="481d9-118">`FFIsEmpty` という名前のブール変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="481d9-118">Create a Boolean variable named `FFIsEmpty`.</span></span>  
  
4.  <span data-ttu-id="481d9-119">スクリプト タスクの **ReadOnlyVariables** プロパティに `FFNonDataRows` 変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="481d9-119">Add the `FFNonDataRows` variable to the Script task's **ReadOnlyVariables** property.</span></span>  
  
5.  <span data-ttu-id="481d9-120">スクリプト タスクの **ReadWriteVariables** プロパティに `FFIsEmpty` 変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="481d9-120">Add the `FFIsEmpty` variable to the Script task's **ReadWriteVariables** property.</span></span>  
  
6.  <span data-ttu-id="481d9-121">コードに `System.IO` 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="481d9-121">In your code, import the `System.IO` namespace.</span></span>  
  
 <span data-ttu-id="481d9-122">単一のフラット ファイル接続マネージャーを使用する代わりに、Foreach File 列挙子を含むファイルを繰り返し処理する場合、接続マネージャーからではなく列挙値が格納される変数からファイル名とパスを取得するように、次のサンプル コードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="481d9-122">If you are iterating over files with a Foreach File enumerator, instead of using a single Flat File connection manager, you will need to modify the sample code below to obtain the file name and path from the variable in which the enumerated value is stored instead of from the connection manager.</span></span>  
  
### <a name="code"></a><span data-ttu-id="481d9-123">コード</span><span class="sxs-lookup"><span data-stu-id="481d9-123">Code</span></span>  
  
```vb  
Public Sub Main()  
  
  Dim nonDataRows As Integer = _  
      DirectCast(Dts.Variables("FFNonDataRows").Value, Integer)  
  Dim ffConnection As String = _  
      DirectCast(Dts.Connections("EmptyFlatFileTest").AcquireConnection(Nothing), _  
      String)  
  Dim flatFileInfo As New FileInfo(ffConnection)  
  ' If file size is 0 bytes, flat file does not contain data.  
  Dim fileSize As Long = flatFileInfo.Length  
  If fileSize > 0 Then  
    Dim lineCount As Integer = 0  
    Dim line As String  
    Dim fsFlatFile As New StreamReader(ffConnection)  
    Do Until fsFlatFile.EndOfStream  
      line = fsFlatFile.ReadLine  
      lineCount += 1  
      ' If line count > expected number of non-data rows,  
      '  flat file contains data (default value).  
      If lineCount > nonDataRows Then  
        Exit Do  
      End If  
      ' If line count <= expected number of non-data rows,  
      '  flat file does not contain data.  
      If lineCount <= nonDataRows Then  
        Dts.Variables("FFIsEmpty").Value = True  
      End If  
    Loop  
  Else  
    Dts.Variables("FFIsEmpty").Value = True  
  End If  
  
  Dim fireAgain As Boolean = False  
  Dts.Events.FireInformation(0, "Script Task", _  
      String.Format("{0}: {1}", ffConnection, _  
      Dts.Variables("FFIsEmpty").Value.ToString), _  
      String.Empty, 0, fireAgain)  
  
  Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
public void Main()  
        {  
  
            int nonDataRows = (int)(Dts.Variables["FFNonDataRows"].Value);  
            string ffConnection = (string)(Dts.Connections["EmptyFlatFileTest"].AcquireConnection(null) as String);  
            FileInfo flatFileInfo = new FileInfo(ffConnection);  
            // If file size is 0 bytes, flat file does not contain data.  
            long fileSize = flatFileInfo.Length;  
            if (fileSize > 0)  
            {  
  
                int lineCount = 0;  
                string line;  
                StreamReader fsFlatFile = new StreamReader(ffConnection);  
                while (!(fsFlatFile.EndOfStream))  
                {  
                    Console.WriteLine (fsFlatFile.ReadLine());  
                    lineCount += 1;  
                    // If line count > expected number of non-data rows,  
                    //  flat file contains data (default value).  
                    if (lineCount > nonDataRows)  
                    {  
                        break;  
                    }  
                    // If line count <= expected number of non-data rows,  
                    //  flat file does not contain data.  
                    if (lineCount <= nonDataRows)  
                    {  
                        Dts.Variables["FFIsEmpty"].Value = true;  
                    }  
                }  
            }  
            else  
            {  
                Dts.Variables["FFIsEmpty"].Value = true;  
            }  
  
            bool fireAgain = false;  
            Dts.Events.FireInformation(0, "Script Task", String.Format("{0}: {1}", ffConnection, Dts.Variables["FFIsEmpty"].Value), String.Empty, 0, ref fireAgain);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
```  
  
<span data-ttu-id="481d9-124">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="481d9-124">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="481d9-125">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="481d9-125">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="481d9-126">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="481d9-126">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="481d9-127">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="481d9-127">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481d9-128">参照</span><span class="sxs-lookup"><span data-stu-id="481d9-128">See Also</span></span>  
 [<span data-ttu-id="481d9-129">スクリプト タスクの例</span><span class="sxs-lookup"><span data-stu-id="481d9-129">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)  
  
  
