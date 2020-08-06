---
title: スクリプト タスクでの変数の使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2cd8fee5741c3d0e28e52c8712c3896428a05e8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743385"
---
# <a name="using-variables-in-the-script-task"></a><span data-ttu-id="32c5f-102">スクリプト タスクでの変数の使用</span><span class="sxs-lookup"><span data-stu-id="32c5f-102">Using Variables in the Script Task</span></span>
  <span data-ttu-id="32c5f-103">スクリプト タスクで変数を使用すると、パッケージ内の別のオブジェクトとデータを交換できます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-103">Variables make it possible for the Script task to exchange data with other objects in the package.</span></span> <span data-ttu-id="32c5f-104">詳細については、「 [Integration Services &#40;SSIS&#41; の変数](../../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c5f-104">For more information, see [Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md).</span></span>  
  
 <span data-ttu-id="32c5f-105">スクリプト タスクは、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを使用して、パッケージ内の <xref:Microsoft.SqlServer.Dts.Runtime.Variable> オブジェクトからデータを読み取ったり、オブジェクトにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-105">The Script task uses the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object to read from and write to <xref:Microsoft.SqlServer.Dts.Runtime.Variable> objects in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32c5f-106"><xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> クラスの <xref:Microsoft.SqlServer.Dts.Runtime.Variable> プロパティのデータ型は `Object` です。</span><span class="sxs-lookup"><span data-stu-id="32c5f-106">The <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.Variable> class is of type `Object`.</span></span> <span data-ttu-id="32c5f-107">スクリプト タスクでは `Option Strict` が有効なので、使用する前に、<xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> プロパティを適切な型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-107">Because the Script task has `Option Strict` enabled, you must cast the <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> property to the appropriate type before you can use it.</span></span>  
  
 <span data-ttu-id="32c5f-108">既存の変数は、**[スクリプト タスク エディター]** の <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> の一覧および <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> の一覧に追加することにより、カスタム スクリプトで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-108">You add existing variables to the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> and <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> lists in the **Script Task Editor** to make them available to the custom script.</span></span> <span data-ttu-id="32c5f-109">変数名の大文字と小文字は区別されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="32c5f-109">Keep in mind that variable names are case-sensitive.</span></span> <span data-ttu-id="32c5f-110">スクリプト内では、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを介して、両方の種類の変数にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-110">Within the script, you access variables of both types through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="32c5f-111">`Value` プロパティを使用して、各変数に対する読み取りおよび書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="32c5f-111">Use the `Value` property to read from and write to individual variables.</span></span> <span data-ttu-id="32c5f-112">スクリプト タスクは、スクリプトが変数の値を読み取ったり変更するときに、ユーザーに意識させずにロックを管理します。</span><span class="sxs-lookup"><span data-stu-id="32c5f-112">The Script task transparently manages locking as the script reads and modifies the values of variables.</span></span>  
  
 <span data-ttu-id="32c5f-113"><xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> プロパティによって返される <xref:Microsoft.SqlServer.Dts.Runtime.Variables> コレクションの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> メソッドを使用すると、変数をコードで使用する前に、その変数の存在を確認できます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-113">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Variables> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property to check for the existence of a variable before using it in your code.</span></span>  
  
 <span data-ttu-id="32c5f-114">スクリプト タスクで変数を扱うには、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> プロパティ (Dts.VariableDispenser) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-114">You can also use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property (Dts.VariableDispenser) to work with variables in the Script task.</span></span> <span data-ttu-id="32c5f-115"><xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> を使用する場合は、コード内で、ロック セマンティクスと、変数値のデータ型のキャストの両方を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-115">When using the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>, you must handle both the locking semantics and the casting of data types for variable values in your own code.</span></span> <span data-ttu-id="32c5f-116">デザイン時には使用できないが、実行時にプログラムによって生成される変数を扱う必要がある場合は、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> プロパティではなく、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを使用する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-116">You may need to use the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> property instead of the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property if you want to work with a variable that is not available at design time but is created programmatically at run time.</span></span>  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a><span data-ttu-id="32c5f-117">Foreach ループ コンテナー内でのスクリプト タスクの使用</span><span class="sxs-lookup"><span data-stu-id="32c5f-117">Using the Script Task within a Foreach Loop Container</span></span>  
 <span data-ttu-id="32c5f-118">Foreach ループ コンテナー内でスクリプト タスクを繰り返し実行する場合、そのスクリプトは通常、列挙子内の現在のアイテムの内容を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-118">When a Script task runs repeatedly within a Foreach Loop container, the script usually needs to work with the contents of the current item in the enumerator.</span></span> <span data-ttu-id="32c5f-119">たとえば、Foreach File 列挙子を使用する場合、スクリプトは現在のファイル名を取得する必要があります。また、Foreach ADO 列挙子を使用する場合、スクリプトは現在のデータ行の列の内容を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-119">For example, when using a Foreach File enumerator, the script needs to know the current file name; when using a Foreach ADO enumerator, the script needs to know the contents of the columns in the current row of data.</span></span>  
  
 <span data-ttu-id="32c5f-120">変数を使用すると、Foreach ループ コンテナーとスクリプト タスク間のこうしたやり取りが可能になります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-120">Variables make this communication between the Foreach Loop container and the Script task possible.</span></span> <span data-ttu-id="32c5f-121">**[Foreach ループ エディター]** の **[変数のマッピング]** ページでは、単一の列挙アイテムによって返されたデータの各アイテムに、変数が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-121">On the **Variable Mappings** page of the **Foreach Loop Editor**, assign variables to each item of data that is returned by a single enumerated item.</span></span> <span data-ttu-id="32c5f-122">たとえば、Foreach File 列挙子の場合は、ファイル名のみがインデックス 0 で返されるためマッピングが必要な変数は 1 つのみですが、各行の複数のデータ列を返す列挙子の場合は、スクリプト タスクで使用する各列に、個別の変数をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-122">For example, a Foreach File enumerator returns only a file name at Index 0 and therefore requires only one variable mapping, whereas an enumerator that returns several columns of data in each row requires you to map a different variable to each column that you want to use in the Script task.</span></span>  
  
 <span data-ttu-id="32c5f-123">列挙された項目を変数にマップしたら、[スクリプト `ReadOnlyVariables` **タスクエディター** ] の [**スクリプト**] ページで、マップされた変数をプロパティに追加して、スクリプトで使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-123">After you have mapped enumerated items to variables, then you must add the mapped variables to the `ReadOnlyVariables` property on the **Script** page of the **Script Task Editor** to make them available to your script.</span></span> <span data-ttu-id="32c5f-124">フォルダー内の画像ファイルを処理する Foreach ループ コンテナー内のスクリプト タスクの例については、「[スクリプト タスクによる画像の操作](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c5f-124">For an example of a Script task within a Foreach Loop container that processes the image files in a folder, see [Working with Images with the Script Task](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md).</span></span>  
  
## <a name="variables-example"></a><span data-ttu-id="32c5f-125">変数の例</span><span class="sxs-lookup"><span data-stu-id="32c5f-125">Variables Example</span></span>  
 <span data-ttu-id="32c5f-126">次の例では、スクリプト タスク内の変数にアクセスし、その変数を使用してパッケージ ワークフローのパスを決定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="32c5f-126">The following example demonstrates how to access and use variables in a Script task to determine the path of package workflow.</span></span> <span data-ttu-id="32c5f-127">このサンプルでは、とという名前の整数変数を作成し、[ `CustomerCount` `MaxRecordCount` `ReadOnlyVariables` **スクリプトタスクエディター**] でコレクションに追加したことを前提としています。</span><span class="sxs-lookup"><span data-stu-id="32c5f-127">The sample assumes that you have created integer variables named `CustomerCount` and `MaxRecordCount` and added them to the `ReadOnlyVariables` collection in the **Script Task Editor**.</span></span> <span data-ttu-id="32c5f-128">`CustomerCount` 変数には、インポートされる顧客レコードの数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-128">The `CustomerCount` variable contains the number of customer records to be imported.</span></span> <span data-ttu-id="32c5f-129">この値が `MaxRecordCount` の値よりも大きい場合、スクリプト タスクから失敗が報告されます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-129">If its value is greater than the value of `MaxRecordCount`, the Script task reports failure.</span></span> <span data-ttu-id="32c5f-130">`MaxRecordCount` のしきい値を超過したために失敗が発生した場合、ワークフローのエラー パスには、任意の必要なクリーンアップを実装できます。</span><span class="sxs-lookup"><span data-stu-id="32c5f-130">When a failure occurs because the `MaxRecordCount` threshold has been exceeded, the error path of the workflow can implement any required clean-up.</span></span>  
  
 <span data-ttu-id="32c5f-131">サンプルを正常にコンパイルするには、Microsoft.SqlServer.ScriptTask アセンブリへの参照を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32c5f-131">To successfully compile the sample, you need to add a reference to the Microsoft.SqlServer.ScriptTask assembly.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
<span data-ttu-id="32c5f-132">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="32c5f-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="32c5f-133">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32c5f-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="32c5f-134">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="32c5f-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="32c5f-135">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="32c5f-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c5f-136">参照</span><span class="sxs-lookup"><span data-stu-id="32c5f-136">See Also</span></span>  
 <span data-ttu-id="32c5f-137">[Integration Services &#40;SSIS&#41; の変数](../../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="32c5f-137">[Integration Services &#40;SSIS&#41; Variables](../../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="32c5f-138">パッケージで変数を使用する</span><span class="sxs-lookup"><span data-stu-id="32c5f-138">Use Variables in Packages</span></span>](../../use-variables-in-packages.md)  
  
  
