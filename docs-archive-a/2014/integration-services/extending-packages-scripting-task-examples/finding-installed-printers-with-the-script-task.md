---
title: スクリプト タスクによるインストールされたプリンターの検索 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- System.Drawing.Printing namespace
- printers [Integration Services]
- SSIS Script task, printers
- locating printers
- Printing namespace
- Script task [Integration Services], examples
- finding printers [SQL Server]
- Script task [Integration Services], printers
ms.assetid: 50a55014-e2c3-4ecd-84e1-3e877c55a260
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cc4bc06879a55d4d07afca1011cc479dd7e7903a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736607"
---
# <a name="finding-installed-printers-with-the-script-task"></a><span data-ttu-id="51363-102">スクリプト タスクによるインストールされたプリンターの検索</span><span class="sxs-lookup"><span data-stu-id="51363-102">Finding Installed Printers with the Script Task</span></span>
  <span data-ttu-id="51363-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージで変換されたデータは、最後の変換先で印刷レポートになることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="51363-103">The data that is transformed by [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages often has a printed report as its final destination.</span></span> <span data-ttu-id="51363-104">`System.Drawing.Printing`の名前空間は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] プリンターを操作するためのクラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="51363-104">The `System.Drawing.Printing` namespace in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] provides classes for working with printers.</span></span>

> [!NOTE]
>  <span data-ttu-id="51363-105">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="51363-105">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="51363-106">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51363-106">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>

## <a name="description"></a><span data-ttu-id="51363-107">説明</span><span class="sxs-lookup"><span data-stu-id="51363-107">Description</span></span>
 <span data-ttu-id="51363-108">次の例では、米国で使用されているリーガル サイズの用紙をサポートしているプリンターがサーバーにインストールされている場合、そのプリンターを検索します。</span><span class="sxs-lookup"><span data-stu-id="51363-108">The following example locates printers installed on the server that support legal size paper (as used in the United States).</span></span> <span data-ttu-id="51363-109">サポートされる用紙サイズを調べるコードは、private 関数にカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="51363-109">The code to check supported paper sizes is encapsulated in a private function.</span></span> <span data-ttu-id="51363-110">各プリンターの設定を確認する間にスクリプトの進行状況を追跡できるように、スクリプトでは <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを使用して、リーガル サイズ用紙をサポートするプリンターには情報メッセージを出力し、リーガル サイズ用紙をサポートしないプリンターには警告メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="51363-110">To enable you to track the progress of the script as it checks the settings for each printer, the script uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> method to raise an informational message for printers with legal size paper, and to raise a warning for printers without legal size paper.</span></span> <span data-ttu-id="51363-111">デザイナーでパッケージを実行すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE の **[出力]** ウィンドウにこれらのメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="51363-111">These messages appear in the **Output** window of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) IDE when you run the package in the designer.</span></span>

#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="51363-112">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="51363-112">To configure this Script Task example</span></span>

1.  <span data-ttu-id="51363-113">`PrinterList` という名前の、`Object` 型の変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="51363-113">Create the variable named `PrinterList` with type `Object`.</span></span>

2.  <span data-ttu-id="51363-114">**[スクリプト タスク エディター]** の **[スクリプト]** ページで、ReadWriteVariables プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="51363-114">On the **Script** page of the **Script Task Editor**, add this variable to the ReadWriteVariables property.</span></span>

3.  <span data-ttu-id="51363-115">このスクリプト プロジェクトでは、参照を **System.Drawing** 名前空間に追加します。</span><span class="sxs-lookup"><span data-stu-id="51363-115">In the script project, add a reference to the **System.Drawing** namespace.</span></span>

4.  <span data-ttu-id="51363-116">コードでは、ステートメントを使用して、 `Imports` **システムコレクション**と名前空間をインポートし `System.Drawing.Printing` ます。</span><span class="sxs-lookup"><span data-stu-id="51363-116">In your code, use `Imports` statements to import the **System.Collections** and the `System.Drawing.Printing` namespaces.</span></span>

### <a name="code"></a><span data-ttu-id="51363-117">コード</span><span class="sxs-lookup"><span data-stu-id="51363-117">Code</span></span>

```vb
Public Sub Main()

    Dim printerName As String
    Dim currentPrinter As New PrinterSettings
    Dim size As PaperSize

    Dim printerList As New ArrayList
    For Each printerName In PrinterSettings.InstalledPrinters
        currentPrinter.PrinterName = printerName
        If PrinterHasLegalPaper(currentPrinter) Then
            printerList.Add(printerName)
            Dts.Events.FireInformation(0, "Example", _
                "Printer " & printerName & " has legal paper.", _
                String.Empty, 0, False)
        Else
            Dts.Events.FireWarning(0, "Example", _
                "Printer " & printerName & " DOES NOT have legal paper.", _
                String.Empty, 0)
        End If
    Next

    Dts.Variables("PrinterList").Value = printerList

    Dts.TaskResult = ScriptResults.Success

End Sub

Private Function PrinterHasLegalPaper( _
    ByVal thisPrinter As PrinterSettings) As Boolean

    Dim size As PaperSize
    Dim hasLegal As Boolean = False

    For Each size In thisPrinter.PaperSizes
        If size.Kind = PaperKind.Legal Then
            hasLegal = True
        End If
    Next

    Return hasLegal

End Function
```

```csharp
public void Main()
        {

            PrinterSettings currentPrinter = new PrinterSettings();
            PaperSize size;
            Boolean Flag = false;

            ArrayList printerList = new ArrayList();
            foreach (string printerName in PrinterSettings.InstalledPrinters)
            {
                currentPrinter.PrinterName = printerName;
                if (PrinterHasLegalPaper(currentPrinter))
                {
                    printerList.Add(printerName);
                    Dts.Events.FireInformation(0, "Example", "Printer " + printerName + " has legal paper.", String.Empty, 0, ref Flag);
                }
                else
                {
                    Dts.Events.FireWarning(0, "Example", "Printer " + printerName + " DOES NOT have legal paper.", String.Empty, 0);
                }
            }

            Dts.Variables["PrinterList"].Value = printerList;

            Dts.TaskResult = (int)ScriptResults.Success;

        }

        private bool PrinterHasLegalPaper(PrinterSettings thisPrinter)
        {

            bool hasLegal = false;

            foreach (PaperSize size in thisPrinter.PaperSizes)
            {
                if (size.Kind == PaperKind.Legal)
                {
                    hasLegal = true;
                }
            }

            return hasLegal;

        }
```

<span data-ttu-id="51363-118">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="51363-118">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="51363-119">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51363-119">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="51363-120">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="51363-120">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="51363-121">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="51363-121">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="51363-122">参照</span><span class="sxs-lookup"><span data-stu-id="51363-122">See Also</span></span>
 [<span data-ttu-id="51363-123">スクリプト タスクの例</span><span class="sxs-lookup"><span data-stu-id="51363-123">Script Task Examples</span></span>](../extending-packages-scripting-task-examples/script-task-examples.md)


