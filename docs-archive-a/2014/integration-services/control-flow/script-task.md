---
title: スクリプト タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.f1
helpviewer_keywords:
- scripts [Integration Services], tasks
- Script task [Integration Services], about Script task
- Script task [Integration Services]
ms.assetid: f6cce7df-4bd6-4b75-9f89-6c37b4bb5558
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 69c051994eb06cbab041db3db2683a487a6e1994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631189"
---
# <a name="script-task"></a><span data-ttu-id="0c769-102">スクリプト タスク</span><span class="sxs-lookup"><span data-stu-id="0c769-102">Script Task</span></span>
  <span data-ttu-id="0c769-103">スクリプト タスクでは、組み込みのタスクで利用できない関数を実行するコード、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] で用意されている変換を実行するコードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0c769-103">The Script task provides code to perform functions that are not available in the built-in tasks and transformations that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="0c769-104">また、スクリプト タスクを使用すると、複数のタスクおよび変換を使用しなくても、関数を 1 つのスクリプトに結合できます。</span><span class="sxs-lookup"><span data-stu-id="0c769-104">The Script task can also combine functions in one script instead of using multiple tasks and transformations.</span></span> <span data-ttu-id="0c769-105">スクリプト タスクは、データ行ごとに 1 回ではなく、1 つのパッケージ内で 1 回 (または列挙されたオブジェクトごとに 1 回) 行う作業に使用します。</span><span class="sxs-lookup"><span data-stu-id="0c769-105">You use the Script task for work that must be done once in a package (or once per enumerated object), instead than once per data row.</span></span>  
  
 <span data-ttu-id="0c769-106">スクリプト タスクは、次の目的で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0c769-106">You can use the Script task for the following purposes:</span></span>  
  
-   <span data-ttu-id="0c769-107">組み込みの接続の種類ではサポートされていないその他のテクノロジを使用して、データにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0c769-107">Access data by using other technologies that are not supported by built-in connection types.</span></span> <span data-ttu-id="0c769-108">たとえば、スクリプトは、Active Directory Service Interfaces (ADSI) を使用して Active Directory のユーザー名にアクセスし、ユーザー名を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="0c769-108">For example, a script can use Active Directory Service Interfaces (ADSI) to access and extract user names from Active Directory.</span></span>  
  
-   <span data-ttu-id="0c769-109">パッケージ固有のパフォーマンス カウンターを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c769-109">Create a package-specific performance counter.</span></span> <span data-ttu-id="0c769-110">たとえば、スクリプトを使用して、複雑なタスクや時間のかかるタスクの実行中に更新されるパフォーマンス カウンターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0c769-110">For example, a script can create a performance counter that is updated while a complex or poorly performing task runs.</span></span>  
  
-   <span data-ttu-id="0c769-111">指定されたファイルが空かどうか、またはそれらのファイルに含まれている行数を判断し、その情報に基づいて、パッケージ内の制御フローを調整します。</span><span class="sxs-lookup"><span data-stu-id="0c769-111">Identify whether specified files are empty or how many rows they contain, and then based on that information affect the control flow in a package.</span></span> <span data-ttu-id="0c769-112">たとえば、ファイル内の行数が 0 行の場合は、変数の値が 0 に設定され、値を評価する優先順位制約で、ファイル システム タスクによるファイルのコピーが回避されます。</span><span class="sxs-lookup"><span data-stu-id="0c769-112">For example, if a file contains zero rows, the value of a variable set to 0, and a precedence constraint that evaluates the value prevents a File System task from copying the file.</span></span>  
  
 <span data-ttu-id="0c769-113">スクリプトを使用してセット内のデータ行ごとに同じ作業を行う必要がある場合は、スクリプト タスクではなく、スクリプト コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0c769-113">If you have to use the script to do the same work for each row of data in a set, you should use the Script component instead of the Script task.</span></span> <span data-ttu-id="0c769-114">たとえば、郵送料が妥当かどうかを評価し、極端に高いデータ行や極端に安いデータ行をスキップする場合は、スクリプト コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0c769-114">For example, if you want to assess the reasonableness of a postage amount and skip data rows that have very high or low amounts, you would use a Script component.</span></span> <span data-ttu-id="0c769-115">詳細については、「 [Script Component](../data-flow/transformations/script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-115">For more information, see [Script Component](../data-flow/transformations/script-component.md).</span></span>  
  
 <span data-ttu-id="0c769-116">複数のパッケージで 1 つのスクリプトを使用する場合は、スクリプト タスクを使用せず、カスタム タスクを記述することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0c769-116">If more than one package uses a script, consider writing a custom task instead of using the Script task.</span></span> <span data-ttu-id="0c769-117">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-117">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
 <span data-ttu-id="0c769-118">スクリプト タスクがパッケージにとって適切な選択である場合、タスクが使用するスクリプトを開発して、タスク自体を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c769-118">After you decide that the Script task is the appropriate choice for your package, you have to both develop the script that the task uses and configure the task itself.</span></span>  
  
## <a name="writing-and-running-the-script-that-the-task-uses"></a><span data-ttu-id="0c769-119">タスクが使用するスクリプトの記述と実行</span><span class="sxs-lookup"><span data-stu-id="0c769-119">Writing and Running the Script that the Task Uses</span></span>  
 <span data-ttu-id="0c769-120">スクリプト タスクでは、スクリプトを記述する環境、およびそのスクリプトを実行するエンジンとして [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c769-120">The Script task uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) as the environment in which you write the scripts and the engine that runs those scripts.</span></span>  
  
 <span data-ttu-id="0c769-121">VSTA には、色分け表示が可能な [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] エディター、IntelliSense、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] オブジェクト エクスプローラー **など、** 環境での標準機能がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c769-121">VSTA provides all the standard features of the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environment, such as the color-coded [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] editor, IntelliSense, and **Object Explorer**.</span></span> <span data-ttu-id="0c769-122">VSTA には、他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] の開発ツールに付属しているのと同じデバッガーも含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c769-122">VSTA also uses the same debugger that other [!INCLUDE[msCoName](../../includes/msconame-md.md)] development tools use.</span></span> <span data-ttu-id="0c769-123">スクリプト内のブレークポイントは、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のタスクやコンテナーのブレークポイントとシームレスに動作します。</span><span class="sxs-lookup"><span data-stu-id="0c769-123">Breakpoints in the script work seamlessly with breakpoints on [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tasks and containers.</span></span> <span data-ttu-id="0c769-124">VSTA では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# の両方のプログラミング言語がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="0c769-124">VSTA supports both the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# programming languages.</span></span>  
  
 <span data-ttu-id="0c769-125">スクリプトを実行するには、パッケージを実行するコンピューターに VSTA がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c769-125">To run a script, you must have VSTA installed on the computer where the package runs.</span></span> <span data-ttu-id="0c769-126">パッケージを実行すると、タスクはスクリプト エンジンを読み込み、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="0c769-126">When the package runs, the task loads the script engine and runs the script.</span></span> <span data-ttu-id="0c769-127">プロジェクト内のアセンブリへの参照を追加すると、スクリプトから外部の .NET アセンブリにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0c769-127">You can access external .NET assemblies in scripts by adding references to the assemblies in the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0c769-128">スクリプトをプリコンパイルするかどうかを指定できた以前のバージョンとは異なり、 [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 以降のバージョンではすべてのスクリプトがプリコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="0c769-128">Unlike earlier versions where you could indicate whether the scripts were precompiled, all scripts are precompiled in [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] and later versions.</span></span> <span data-ttu-id="0c769-129">スクリプトがプリコンパイルされると、実行時に言語エンジンを読み込まないため、パッケージの実行速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="0c769-129">When a script is precompiled, the language engine is not loaded at run time and the package runs more quickly.</span></span> <span data-ttu-id="0c769-130">ただし、コンパイル済みのバイナリ ファイルは多量のディスク領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c769-130">However, precompiled binary files consume significant disk space.</span></span>  
  
## <a name="configuring-the-script-task"></a><span data-ttu-id="0c769-131">スクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="0c769-131">Configuring the Script Task</span></span>  
 <span data-ttu-id="0c769-132">スクリプト タスクは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="0c769-132">You can configure the Script task in the following ways:</span></span>  
  
-   <span data-ttu-id="0c769-133">タスクを実行するカスタム スクリプトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0c769-133">Provide the custom script that the task runs.</span></span>  
  
-   <span data-ttu-id="0c769-134">スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトのメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="0c769-134">Specify the method in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span>  
  
-   <span data-ttu-id="0c769-135">スクリプト言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c769-135">Specify the script language.</span></span>  
  
-   <span data-ttu-id="0c769-136">必要に応じて、スクリプトで使用する読み取り専用の変数および読み取り/書き込み変数の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c769-136">Optionally, provide lists of read-only and read/write variables for use in the script.</span></span>  
  
 <span data-ttu-id="0c769-137">これらのプロパティは [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定するか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="0c769-137">You can set these properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
### <a name="configuring-the-script-task-in-the-designer"></a><span data-ttu-id="0c769-138">デザイナーでのスクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="0c769-138">Configuring the Script Task in the Designer</span></span>  
 <span data-ttu-id="0c769-139">次の表では、スクリプト タスクでログに記録できる `ScriptTaskLogEntry` イベントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0c769-139">The following table describes the `ScriptTaskLogEntry` event that can be logged for Script task.</span></span> <span data-ttu-id="0c769-140">`ScriptTaskLogEntry`イベントは、[ **SSIS ログの構成**] ダイアログボックスの [**詳細**] タブで、ログ記録の対象として選択されます。</span><span class="sxs-lookup"><span data-stu-id="0c769-140">The `ScriptTaskLogEntry` event is selected for logging on the **Details** tab of the **Configure SSIS Logs** dialog box.</span></span> <span data-ttu-id="0c769-141">詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../custom-messages-for-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0c769-141">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md) and [Custom Messages for Logging](../custom-messages-for-logging.md).</span></span>  
  
|<span data-ttu-id="0c769-142">ログ エントリ</span><span class="sxs-lookup"><span data-stu-id="0c769-142">Log entry</span></span>|<span data-ttu-id="0c769-143">説明</span><span class="sxs-lookup"><span data-stu-id="0c769-143">Description</span></span>|  
|---------------|-----------------|  
|`ScriptTaskLogEntry`|<span data-ttu-id="0c769-144">スクリプト内でのログ記録の実装結果を報告します。</span><span class="sxs-lookup"><span data-stu-id="0c769-144">Reports the results of implementing logging in the script.</span></span> <span data-ttu-id="0c769-145">タスクは、`Log` オブジェクトの `Dts` メソッドを呼び出すたびにログ エントリを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0c769-145">The task writes a log entry for each call to the `Log` method of the `Dts` object.</span></span> <span data-ttu-id="0c769-146">タスクは、これらのエントリをコードの実行時に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0c769-146">The task writes these entries when the code is run.</span></span> <span data-ttu-id="0c769-147">詳細については、「 [スクリプト タスクでのログ記録](../extending-packages-scripting/task/logging-in-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-147">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md).</span></span>|  
  
 <span data-ttu-id="0c769-148">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-148">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topics:</span></span>  
  
-   <span data-ttu-id="0c769-149">[[スクリプト タスク エディター] &#40;[全般] ページ&#41;](../general-page-of-integration-services-designers-options.md)</span><span class="sxs-lookup"><span data-stu-id="0c769-149">[Script Task Editor &#40;General Page&#41;](../general-page-of-integration-services-designers-options.md)</span></span>  
  
-   <span data-ttu-id="0c769-150">[[スクリプト タスク エディター] ([スクリプト] ページ)](../script-task-editor-script-page.md)</span><span class="sxs-lookup"><span data-stu-id="0c769-150">[Script Task Editor &#40;Script Page&#41;](../script-task-editor-script-page.md)</span></span>  
  
-   <span data-ttu-id="0c769-151">[[式] ページ](../expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="0c769-151">[Expressions Page](../expressions/expressions-page.md)</span></span>  
  
 <span data-ttu-id="0c769-152">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-152">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, see the following topic:</span></span>  
  
-   [<span data-ttu-id="0c769-153">タスクまたはコンテナーのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="0c769-153">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
### <a name="configuring-the-script-task-programmatically"></a><span data-ttu-id="0c769-154">プログラムによるスクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="0c769-154">Configuring the Script Task Programmatically</span></span>  
 <span data-ttu-id="0c769-155">プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c769-155">For more information about programmatically setting these properties, see the following topic:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask>  
  
## <a name="related-content"></a><span data-ttu-id="0c769-156">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0c769-156">Related Content</span></span>  
  
-   <span data-ttu-id="0c769-157">shareourideas.com の技術記事「 [配信通知付きで電子メールを送信する方法 (C#)](https://go.microsoft.com/fwlink/?LinkId=237625)」</span><span class="sxs-lookup"><span data-stu-id="0c769-157">Technical article, [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625), on shareourideas.com</span></span>  
  
  
