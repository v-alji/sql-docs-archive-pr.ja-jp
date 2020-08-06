---
title: スクリプト タスクを使用した Excel ファイルの操作 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68a764452de548cd46e74d2a7f2f588a050a21c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641169"
---
# <a name="working-with-excel-files-with-the-script-task"></a><span data-ttu-id="17f80-102">スクリプト タスクを使用した Excel ファイルの操作</span><span class="sxs-lookup"><span data-stu-id="17f80-102">Working with Excel Files with the Script Task</span></span>
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="17f80-103">には Excel 接続マネージャー、Excel ソース、Excel 変換先が用意されており、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel ファイル形式のスプレッドシートに保存されているデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="17f80-103">provides the Excel connection manager, Excel source, and Excel destination for working with data stored in spreadsheets in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel file format.</span></span> <span data-ttu-id="17f80-104">このトピックで説明する方法では、スクリプト タスクを使用して、使用可能な Excel のデータベース (ワークブック ファイル) およびテーブル (ワークシートおよび名前付き範囲) に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="17f80-104">The techniques described in this topic use the Script task to obtain information about available Excel databases (workbook files) and tables (worksheets and named ranges).</span></span> <span data-ttu-id="17f80-105">これらのサンプルに簡単な変更を加えて、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB プロバイダーによってサポートされる他のすべてのファイルベース データ ソースを操作することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-105">These samples can easily be modified to work with any of the other file-based data sources supported by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider.</span></span>  
  
 [<span data-ttu-id="17f80-106">サンプルをテストするためのパッケージの構成</span><span class="sxs-lookup"><span data-stu-id="17f80-106">Configuring a Package to Test the Samples</span></span>](#configuring)  
  
 [<span data-ttu-id="17f80-107">例 1: Excel ファイルが存在するかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="17f80-107">Example1: Check Whether an Excel File Exists</span></span>](#example1)  
  
 [<span data-ttu-id="17f80-108">例 2: Excel テーブルが存在するかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="17f80-108">Example 2: Check Whether an Excel Table Exists</span></span>](#example2)  
  
 [<span data-ttu-id="17f80-109">例 3: フォルダー内の Excel ファイルの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="17f80-109">Example 3: Get a List of Excel Files in a Folder</span></span>](#example3)  
  
 [<span data-ttu-id="17f80-110">例 4: Excel ファイル内のテーブルの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="17f80-110">Example 4: Get a List of Tables in an Excel File</span></span>](#example4)  
  
 [<span data-ttu-id="17f80-111">サンプルの結果の表示</span><span class="sxs-lookup"><span data-stu-id="17f80-111">Displaying the Results of the Samples</span></span>](#testing)  
  
> [!NOTE]  
>  <span data-ttu-id="17f80-112">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-112">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="17f80-113">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-113">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="configuring-a-package-to-test-the-samples"></a><a name="configuring"></a><span data-ttu-id="17f80-114">サンプルをテストするためのパッケージの構成</span><span class="sxs-lookup"><span data-stu-id="17f80-114">Configuring a Package to Test the Samples</span></span>  
 <span data-ttu-id="17f80-115">このトピックのすべてのサンプルをテストする単一のパッケージを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-115">You can configure a single package to test all the samples in this topic.</span></span> <span data-ttu-id="17f80-116">これらのサンプルでは、同じパッケージ変数と同じ [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] クラスを数多く使用します。</span><span class="sxs-lookup"><span data-stu-id="17f80-116">The samples use many of the same package variables and the same [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] classes.</span></span>  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a><span data-ttu-id="17f80-117">このトピックの例で使用するパッケージを構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-117">To configure a package for use with the examples in this topic</span></span>  
  
1.  <span data-ttu-id="17f80-118">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で新しい [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] プロジェクトを作成し、編集のために既定のパッケージを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-118">Create a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and open the default package for editing.</span></span>  
  
2.  <span data-ttu-id="17f80-119">**変数**。</span><span class="sxs-lookup"><span data-stu-id="17f80-119">**Variables**.</span></span> <span data-ttu-id="17f80-120">**[変数]** ウィンドウを開き、次の変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="17f80-120">Open the **Variables** window and define the following variables:</span></span>  
  
    -   <span data-ttu-id="17f80-121">`String` 型の `ExcelFile`。</span><span class="sxs-lookup"><span data-stu-id="17f80-121">`ExcelFile`, of type `String`.</span></span> <span data-ttu-id="17f80-122">既存の Excel ワークブックの完全なパスとファイル名を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-122">Enter the complete path and filename to an existing Excel workbook.</span></span>  
  
    -   <span data-ttu-id="17f80-123">`String` 型の `ExcelTable`。</span><span class="sxs-lookup"><span data-stu-id="17f80-123">`ExcelTable`, of type `String`.</span></span> <span data-ttu-id="17f80-124">`ExcelFile` 変数の値で指定されたワークブック内の既存のワークシートまたは名前付き範囲の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-124">Enter the name of an existing worksheet or named range in the workbook named in the value of the `ExcelFile` variable.</span></span> <span data-ttu-id="17f80-125">この値は、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="17f80-125">This value is case-sensitive.</span></span>  
  
    -   <span data-ttu-id="17f80-126">`Boolean` 型の `ExcelFileExists`。</span><span class="sxs-lookup"><span data-stu-id="17f80-126">`ExcelFileExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="17f80-127">`Boolean` 型の `ExcelTableExists`。</span><span class="sxs-lookup"><span data-stu-id="17f80-127">`ExcelTableExists`, of type `Boolean`.</span></span>  
  
    -   <span data-ttu-id="17f80-128">`String` 型の `ExcelFolder`。</span><span class="sxs-lookup"><span data-stu-id="17f80-128">`ExcelFolder`, of type `String`.</span></span> <span data-ttu-id="17f80-129">少なくとも 1 つの Excel ワークブックを含むフォルダーの完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-129">Enter the complete path of a folder that contains at least one Excel workbook.</span></span>  
  
    -   <span data-ttu-id="17f80-130">`Object` 型の `ExcelFiles`。</span><span class="sxs-lookup"><span data-stu-id="17f80-130">`ExcelFiles`, of type `Object`.</span></span>  
  
    -   <span data-ttu-id="17f80-131">`Object` 型の `ExcelTables`。</span><span class="sxs-lookup"><span data-stu-id="17f80-131">`ExcelTables`, of type `Object`.</span></span>  
  
3.  <span data-ttu-id="17f80-132">**ステートメントをインポート**します。</span><span class="sxs-lookup"><span data-stu-id="17f80-132">**Imports statements**.</span></span> <span data-ttu-id="17f80-133">ほとんどのコード サンプルでは、スクリプト ファイルの先頭で次の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 名前空間のいずれかまたは両方をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17f80-133">Most of the code samples require you to import one or both of the following [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] namespaces at the top of your script file:</span></span>  
  
    -   <span data-ttu-id="17f80-134">ファイル システム操作用の `System.IO`。</span><span class="sxs-lookup"><span data-stu-id="17f80-134">`System.IO`, for file system operations.</span></span>  
  
    -   <span data-ttu-id="17f80-135">Excel ファイルをデータ ソースとして開くための `System.Data.OleDb`。</span><span class="sxs-lookup"><span data-stu-id="17f80-135">`System.Data.OleDb`, to open Excel files as data sources.</span></span>  
  
4.  <span data-ttu-id="17f80-136">**参照**。</span><span class="sxs-lookup"><span data-stu-id="17f80-136">**References**.</span></span> <span data-ttu-id="17f80-137">Excel ファイルからスキーマ情報を読み取るコード サンプルでは、スクリプト プロジェクトで `System.Xml` 名前空間への追加の参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="17f80-137">The code samples that read schema information from Excel files require an additional reference in the script project to the `System.Xml` namespace.</span></span>  
  
5.  <span data-ttu-id="17f80-138">**[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用して、スクリプト コンポーネントの既定のスクリプト言語を設定します。</span><span class="sxs-lookup"><span data-stu-id="17f80-138">Set the default scripting language for the Script component by using the **Scripting language** option on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="17f80-139">詳細については、「 [General Page](../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-139">For more information, see [General Page](../general-page-of-integration-services-designers-options.md).</span></span>  
  
##  <a name="example-1-description-check-whether-an-excel-file-exists"></a><a name="example1"></a> <span data-ttu-id="17f80-140">例 1 の説明: Excel ファイルが存在するかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="17f80-140">Example 1 Description: Check Whether an Excel File Exists</span></span>  
 <span data-ttu-id="17f80-141">この例では、`ExcelFile` 変数で指定された Excel ワークブック ファイルが存在するかどうかを判断し、その結果を `ExcelFileExists` 変数のブール値に設定します。</span><span class="sxs-lookup"><span data-stu-id="17f80-141">This example determines whether the Excel workbook file specified in the `ExcelFile` variable exists, and then sets the Boolean value of the `ExcelFileExists` variable to the result.</span></span> <span data-ttu-id="17f80-142">このブール値は、パッケージのワークフローを分岐させるために使用することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-142">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="17f80-143">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-143">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="17f80-144">パッケージに新しいスクリプトタスクを追加し、名前をに変更し `ExcelFileExists` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-144">Add a new Script task to the package and change its name to `ExcelFileExists`.</span></span>  
  
2.  <span data-ttu-id="17f80-145">**[スクリプト タスク エディター]** の **[スクリプト]** タブで **[ReadOnlyVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-145">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-146">「`ExcelFile`.</span><span class="sxs-lookup"><span data-stu-id="17f80-146">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="17f80-147">または</span><span class="sxs-lookup"><span data-stu-id="17f80-147">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-148">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで変数を選択し `ExcelFile` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-148">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFile` variable.</span></span>  
  
3.  <span data-ttu-id="17f80-149">**[ReadWriteVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-149">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-150">「`ExcelFileExists`.</span><span class="sxs-lookup"><span data-stu-id="17f80-150">Type `ExcelFileExists`.</span></span>  
  
         <span data-ttu-id="17f80-151">または</span><span class="sxs-lookup"><span data-stu-id="17f80-151">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-152">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで変数を選択し `ExcelFileExists` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-152">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelFileExists` variable.</span></span>  
  
4.  <span data-ttu-id="17f80-153">**[スクリプトの編集]** をクリックして、スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-153">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="17f80-154">スクリプト ファイルの先頭に、`Imports` 名前空間の `System.IO` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-154">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="17f80-155">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-155">Add the following code.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="17f80-156">例 1 のコード</span><span class="sxs-lookup"><span data-stu-id="17f80-156">Example 1 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example-2-description-check-whether-an-excel-table-exists"></a><a name="example2"></a> <span data-ttu-id="17f80-157">例 2 の説明: Excel テーブルが存在するかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="17f80-157">Example 2 Description: Check Whether an Excel Table Exists</span></span>  
 <span data-ttu-id="17f80-158">この例では、`ExcelTable` 変数で指定された Excel ワークシートまたは名前付き範囲が `ExcelFile` 変数で指定された Excel ワークブック ファイル内に存在するかどうかを判断し、その結果を `ExcelTableExists` 変数のブール値に設定します。</span><span class="sxs-lookup"><span data-stu-id="17f80-158">This example determines whether the Excel worksheet or named range specified in the `ExcelTable` variable exists in the Excel workbook file specified in the `ExcelFile` variable, and then sets the Boolean value of the `ExcelTableExists` variable to the result.</span></span> <span data-ttu-id="17f80-159">このブール値は、パッケージのワークフローを分岐させるために使用することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-159">You can use this Boolean value for branching in the workflow of the package.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="17f80-160">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-160">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="17f80-161">パッケージに新しいスクリプトタスクを追加し、名前をに変更し `ExcelTableExists` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-161">Add a new Script task to the package and change its name to `ExcelTableExists`.</span></span>  
  
2.  <span data-ttu-id="17f80-162">**[スクリプト タスク エディター]** の **[スクリプト]** タブで **[ReadOnlyVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-162">In the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-163">型 `ExcelTable` を `ExcelFile` コンマで区切って入力します。`.`</span><span class="sxs-lookup"><span data-stu-id="17f80-163">Type `ExcelTable` and `ExcelFile` separated by commas`.`</span></span>  
  
         <span data-ttu-id="17f80-164">または</span><span class="sxs-lookup"><span data-stu-id="17f80-164">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-165">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで、 `ExcelTable` 変数と変数を選択し `ExcelFile` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-165">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTable` and `ExcelFile` variables.</span></span>  
  
3.  <span data-ttu-id="17f80-166">**[ReadWriteVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-166">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-167">「`ExcelTableExists`.</span><span class="sxs-lookup"><span data-stu-id="17f80-167">Type `ExcelTableExists`.</span></span>  
  
         <span data-ttu-id="17f80-168">または</span><span class="sxs-lookup"><span data-stu-id="17f80-168">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-169">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで変数を選択し `ExcelTableExists` ます。</span><span class="sxs-lookup"><span data-stu-id="17f80-169">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the `ExcelTableExists` variable.</span></span>  
  
4.  <span data-ttu-id="17f80-170">**[スクリプトの編集]** をクリックして、スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-170">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="17f80-171">スクリプト プロジェクトに `System.Xml` アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-171">Add a reference to the `System.Xml` assembly in the script project.</span></span>  
  
6.  <span data-ttu-id="17f80-172">スクリプト ファイルの先頭に、`Imports` 名前空間と `System.IO` 名前空間の `System.Data.OleDb` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-172">Add `Imports` statements for the `System.IO` and `System.Data.OleDb` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="17f80-173">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-173">Add the following code.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="17f80-174">例 2 のコード</span><span class="sxs-lookup"><span data-stu-id="17f80-174">Example 2 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example-3-description-get-a-list-of-excel-files-in-a-folder"></a><a name="example3"></a> <span data-ttu-id="17f80-175">例 3 の説明: フォルダー内の Excel ファイルの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="17f80-175">Example 3 Description: Get a List of Excel Files in a Folder</span></span>  
 <span data-ttu-id="17f80-176">この例では、`ExcelFolder` 変数の値で指定されたフォルダー内で検索された Excel ファイルの一覧を配列に代入し、その配列を `ExcelFiles` 変数にコピーします。</span><span class="sxs-lookup"><span data-stu-id="17f80-176">This example fills an array with the list of Excel files found in the folder specified in the value of the `ExcelFolder` variable, and then copies the array into the `ExcelFiles` variable.</span></span> <span data-ttu-id="17f80-177">Foreach from Variable 列挙子を使用して、配列内のファイルを繰り返し処理することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-177">You can use the Foreach from Variable enumerator to iterate over the files in the array.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="17f80-178">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-178">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="17f80-179">パッケージに新しいスクリプト タスクを追加し、その名前を **GetExcelFiles** に変更します。</span><span class="sxs-lookup"><span data-stu-id="17f80-179">Add a new Script task to the package and change its name to **GetExcelFiles**.</span></span>  
  
2.  <span data-ttu-id="17f80-180">**[スクリプト タスク エディター]** を開き、**[スクリプト]** タブで **[ReadOnlyVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-180">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-181">「`ExcelFolder`」と入力します</span><span class="sxs-lookup"><span data-stu-id="17f80-181">Type `ExcelFolder`</span></span>  
  
         <span data-ttu-id="17f80-182">または</span><span class="sxs-lookup"><span data-stu-id="17f80-182">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-183">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで [excelfolder] 変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="17f80-183">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFolder variable.</span></span>  
  
3.  <span data-ttu-id="17f80-184">**[ReadWriteVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-184">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-185">「`ExcelFiles`.</span><span class="sxs-lookup"><span data-stu-id="17f80-185">Type `ExcelFiles`.</span></span>  
  
         <span data-ttu-id="17f80-186">または</span><span class="sxs-lookup"><span data-stu-id="17f80-186">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-187">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで [excelfiles] 変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="17f80-187">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFiles variable.</span></span>  
  
4.  <span data-ttu-id="17f80-188">**[スクリプトの編集]** をクリックして、スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-188">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="17f80-189">スクリプト ファイルの先頭に、`Imports` 名前空間の `System.IO` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-189">Add an `Imports` statement for the `System.IO` namespace at the top of the script file.</span></span>  
  
6.  <span data-ttu-id="17f80-190">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-190">Add the following code.</span></span>  
  
### <a name="example-3-code"></a><span data-ttu-id="17f80-191">例 3 のコード</span><span class="sxs-lookup"><span data-stu-id="17f80-191">Example 3 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="17f80-192">代替ソリューション</span><span class="sxs-lookup"><span data-stu-id="17f80-192">Alternate Solution</span></span>  
 <span data-ttu-id="17f80-193">スクリプト タスクを使用して Excel ファイルの一覧を配列に集める代わりに、ForEach File 列挙子を使用してフォルダー内のすべての Excel ファイルを繰り返し処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="17f80-193">Instead of using a Script task to gather a list of Excel files into an array, you can also use the ForEach File enumerator to iterate over all the Excel files in a folder.</span></span> <span data-ttu-id="17f80-194">詳細については、「[Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する方法](../control-flow/foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-194">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="example-4-description-get-a-list-of-tables-in-an-excel-file"></a><a name="example4"></a> <span data-ttu-id="17f80-195">例 4 の説明: Excel ファイル内のテーブルの一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="17f80-195">Example 4 Description: Get a List of Tables in an Excel File</span></span>  
 <span data-ttu-id="17f80-196">この例では、`ExcelFile` 変数の値で指定された Excel ワークブック ファイル内で検索されたワークシートまたは名前付き範囲の一覧を配列に代入し、その配列を `ExcelTables` 変数にコピーします。</span><span class="sxs-lookup"><span data-stu-id="17f80-196">This example fills an array with the list of worksheets and named ranges found in the Excel workbook file specified by the value of the `ExcelFile` variable, and then copies the array into the `ExcelTables` variable.</span></span> <span data-ttu-id="17f80-197">Foreach from Variable 列挙子を使用して、配列内のテーブルを繰り返し処理することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-197">You can use the Foreach from Variable Enumerator to iterate over the tables in the array.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="17f80-198">Excel ブック内のテーブルの一覧には、ワークシート ($ サフィックスが付きます) と名前付き範囲が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17f80-198">The list of tables in an Excel workbook includes both worksheets (which have the $ suffix) and named ranges.</span></span> <span data-ttu-id="17f80-199">ワークシートまたは名前付き範囲のみを一覧からフィルター選択する必要がある場合は、そのためのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17f80-199">If you have to filter the list for only worksheets or only named ranges, you may have to add additional code for this purpose.</span></span>  
  
#### <a name="to-configure-this-script-task-example"></a><span data-ttu-id="17f80-200">このスクリプト タスクの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-200">To configure this Script Task example</span></span>  
  
1.  <span data-ttu-id="17f80-201">パッケージに新しいスクリプト タスクを追加し、その名前を **GetExcelTables** に変更します。</span><span class="sxs-lookup"><span data-stu-id="17f80-201">Add a new Script task to the package and change its name to **GetExcelTables**.</span></span>  
  
2.  <span data-ttu-id="17f80-202">**[スクリプト タスク エディター]** を開き、**[スクリプト]** タブで **[ReadOnlyVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-202">Open the **Script Task Editor**, on the **Script** tab, click **ReadOnlyVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-203">「`ExcelFile`.</span><span class="sxs-lookup"><span data-stu-id="17f80-203">Type `ExcelFile`.</span></span>  
  
         <span data-ttu-id="17f80-204">または</span><span class="sxs-lookup"><span data-stu-id="17f80-204">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-205">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで [excelfile] 変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="17f80-205">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelFile variable.</span></span>  
  
3.  <span data-ttu-id="17f80-206">**[ReadWriteVariables]** をクリックし、次のいずれかの方法でプロパティ値を入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-206">Click **ReadWriteVariables** and enter the property value using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="17f80-207">「`ExcelTables`.</span><span class="sxs-lookup"><span data-stu-id="17f80-207">Type `ExcelTables`.</span></span>  
  
         <span data-ttu-id="17f80-208">または</span><span class="sxs-lookup"><span data-stu-id="17f80-208">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-209">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで [excelitems] 変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="17f80-209">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, select the ExcelTablesvariable.</span></span>  
  
4.  <span data-ttu-id="17f80-210">**[スクリプトの編集]** をクリックして、スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-210">Click **Edit Script** to open the script editor.</span></span>  
  
5.  <span data-ttu-id="17f80-211">スクリプトプロジェクト内の名前空間への参照を追加 `System.Xml` します。</span><span class="sxs-lookup"><span data-stu-id="17f80-211">Add a reference to the `System.Xml` namespace in the script project.</span></span>  
  
6.  <span data-ttu-id="17f80-212">スクリプト ファイルの先頭に、`Imports` 名前空間の `System.Data.OleDb` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-212">Add an `Imports` statement for the `System.Data.OleDb` namespace at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="17f80-213">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-213">Add the following code.</span></span>  
  
### <a name="example-4-code"></a><span data-ttu-id="17f80-214">例 4 のコード</span><span class="sxs-lookup"><span data-stu-id="17f80-214">Example 4 Code</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a><span data-ttu-id="17f80-215">代替ソリューション</span><span class="sxs-lookup"><span data-stu-id="17f80-215">Alternate Solution</span></span>  
 <span data-ttu-id="17f80-216">スクリプト タスクを使用して Excel テーブルの一覧を配列に集める代わりに、ForEach ADO.NET Schema Rowset 列挙子を使用して Excel ワークブック ファイル内のすべてのテーブル (つまり、ワークシートと名前付き範囲) を繰り返し処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="17f80-216">Instead of using a Script task to gather a list of Excel tables into an array, you can also use the ForEach ADO.NET Schema Rowset Enumerator to iterate over all the tables (that is, worksheets and named ranges) in an Excel workbook file.</span></span> <span data-ttu-id="17f80-217">詳細については、「[Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する方法](../control-flow/foreach-loop-container.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-217">For more information, see [Loop through Excel Files and Tables by Using a Foreach Loop Container](../control-flow/foreach-loop-container.md).</span></span>  
  
##  <a name="displaying-the-results-of-the-samples"></a><a name="testing"></a><span data-ttu-id="17f80-218">サンプルの結果を表示する</span><span class="sxs-lookup"><span data-stu-id="17f80-218">Displaying the Results of the Samples</span></span>  
 <span data-ttu-id="17f80-219">このトピックの各例を同じパッケージで構成した場合は、すべてのスクリプト タスクを、すべての例の出力を表示する追加のスクリプト タスクに接続することができます。</span><span class="sxs-lookup"><span data-stu-id="17f80-219">If you have configured each of the examples in this topic in the same package, you can connect all the Script tasks to an additional Script task that displays the output of all the examples.</span></span>  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a><span data-ttu-id="17f80-220">このトピックの例の出力を表示するスクリプト タスクを構成するには</span><span class="sxs-lookup"><span data-stu-id="17f80-220">To configure a Script task to display the output of the examples in this topic</span></span>  
  
1.  <span data-ttu-id="17f80-221">パッケージに新しいスクリプト タスクを追加し、その名前を **DisplayResults** に変更します。</span><span class="sxs-lookup"><span data-stu-id="17f80-221">Add a new Script task to the package and change its name to **DisplayResults**.</span></span>  
  
2.  <span data-ttu-id="17f80-222">4 つのスクリプト タスク例のそれぞれを互いに接続し、各タスクが、前のタスクが正常に完了した後に実行されるようにして、4 番目のタスク例を **DisplayResults** タスクに接続します。</span><span class="sxs-lookup"><span data-stu-id="17f80-222">Connect each of the four example Script tasks to one another, so that each task runs after the preceding task completes successfully, and connect the fourth example task to the **DisplayResults** task.</span></span>  
  
3.  <span data-ttu-id="17f80-223">**[スクリプト タスク エディター]** で **DisplayResults** タスクを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-223">Open the **DisplayResults** task in the **Script Task Editor**.</span></span>  
  
4.  <span data-ttu-id="17f80-224">**[スクリプト]** タブで **[ReadOnlyVariables]** をクリックし、次のいずれかの方法で、「[サンプルをテストするためのパッケージの構成](#configuring)」で一覧表示されている 7 つの変数のすべてを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-224">On the **Script** tab, click **ReadOnlyVariables** and use one of the following methods to add all seven variables listed in [Configuring a Package to Test the Samples](#configuring):</span></span>  
  
    -   <span data-ttu-id="17f80-225">各変数の名前をコンマで区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="17f80-225">Type the name of each variable separated by commas.</span></span>  
  
         <span data-ttu-id="17f80-226">または</span><span class="sxs-lookup"><span data-stu-id="17f80-226">-or-</span></span>  
  
    -   <span data-ttu-id="17f80-227">プロパティフィールドの横にある省略記号ボタン ([**...**]) をクリックし、[**変数の選択**] ダイアログボックスで変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="17f80-227">Click the ellipsis (**...**) button next to the property field, and in the **Select variables** dialog box, selecting the variables.</span></span>  
  
5.  <span data-ttu-id="17f80-228">**[スクリプトの編集]** をクリックして、スクリプト エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="17f80-228">Click **Edit Script** to open the script editor.</span></span>  
  
6.  <span data-ttu-id="17f80-229">スクリプト ファイルの先頭に、`Imports` 名前空間と `Microsoft.VisualBasic` 名前空間の `System.Windows.Forms` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-229">Add `Imports` statements for the `Microsoft.VisualBasic` and `System.Windows.Forms` namespaces at the top of the script file.</span></span>  
  
7.  <span data-ttu-id="17f80-230">次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="17f80-230">Add the following code.</span></span>  
  
8.  <span data-ttu-id="17f80-231">パッケージを実行し、メッセージ ボックスに表示される結果を調べます。</span><span class="sxs-lookup"><span data-stu-id="17f80-231">Run the package and examine the results displayed in a message box.</span></span>  
  
### <a name="code-to-display-the-results"></a><span data-ttu-id="17f80-232">結果を表示するコード</span><span class="sxs-lookup"><span data-stu-id="17f80-232">Code to Display the Results</span></span>  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
<span data-ttu-id="17f80-233">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="17f80-233">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="17f80-234">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="17f80-234">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="17f80-235">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="17f80-235">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="17f80-236">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="17f80-236">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17f80-237">参照</span><span class="sxs-lookup"><span data-stu-id="17f80-237">See Also</span></span>  
 <span data-ttu-id="17f80-238">[Excel 接続マネージャー](../connection-manager/excel-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="17f80-238">[Excel Connection Manager](../connection-manager/excel-connection-manager.md) </span></span>  
 [<span data-ttu-id="17f80-239">Foreach ループ コンテナーを使用して Excel のファイルおよびテーブルをループ処理する</span><span class="sxs-lookup"><span data-stu-id="17f80-239">Loop through Excel Files and Tables by Using a Foreach Loop Container</span></span>](../control-flow/foreach-loop-container.md)  
  
  
