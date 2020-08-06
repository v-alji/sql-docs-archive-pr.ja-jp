---
title: スクリプトタスクエディター ([スクリプト] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.scripttask.script.f1
helpviewer_keywords:
- Script Task Editor
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4eec491cc689d7d5c616e0819075e1ee5159d4e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712154"
---
# <a name="script-task-editor-script-page"></a><span data-ttu-id="544bd-102">[スクリプト タスク エディター] \([スクリプト] ページ)</span><span class="sxs-lookup"><span data-stu-id="544bd-102">Script Task Editor (Script Page)</span></span>
  <span data-ttu-id="544bd-103">**[スクリプト タスク エディター]** ダイアログ ボックスの **[スクリプト]** ページを使用すると、スクリプト プロパティを設定し、スクリプトによってアクセスできる変数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="544bd-103">Use the **Script** page of the **Script Task Editor** dialog box to set script properties and specify variables that can be accessed by the script.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="544bd-104">[!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] およびそれ以降のバージョンでは、すべてのスクリプトがプリコンパイル済みです。</span><span class="sxs-lookup"><span data-stu-id="544bd-104">In [!INCLUDE[ssISversion10](../includes/ssisversion10-md.md)] and later versions, all scripts are precompiled.</span></span> <span data-ttu-id="544bd-105">以前のバージョンでは、 **PrecompileScriptIntoBinaryCode** プロパティを設定して、スクリプトを事前コンパイルするかどうかを指定していました。</span><span class="sxs-lookup"><span data-stu-id="544bd-105">In earlier versions, you set a **PrecompileScriptIntoBinaryCode** property to specify that the script was precompiled.</span></span>  
  
 <span data-ttu-id="544bd-106">スクリプト タスクの詳細については、「 [Script Task](control-flow/script-task.md) 」および「 [スクリプト タスク エディターでのスクリプト タスクの構成](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544bd-106">To learn more about the Script task, see [Script Task](control-flow/script-task.md) and [Configuring the Script Task in the Script Task Editor](extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md).</span></span> <span data-ttu-id="544bd-107">スクリプト タスクのプログラミングの詳細については、「 [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544bd-107">To learn about programming the Script task, see [Extending the Package with the Script Task](extending-packages-scripting/task/extending-the-package-with-the-script-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="544bd-108">Options</span><span class="sxs-lookup"><span data-stu-id="544bd-108">Options</span></span>  
 <span data-ttu-id="544bd-109">**[ScriptLanguage]**</span><span class="sxs-lookup"><span data-stu-id="544bd-109">**ScriptLanguage**</span></span>  
 <span data-ttu-id="544bd-110">タスクのスクリプト言語を選択します。 [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C# のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="544bd-110">Select the scripting language for the task, either [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual C#.</span></span>  
  
 <span data-ttu-id="544bd-111">タスクのスクリプトを作成した後に、 **[ScriptLanguage]** プロパティの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="544bd-111">After you have created a script for the task, you cannot change the value of the **ScriptLanguage** property.</span></span>  
  
 <span data-ttu-id="544bd-112">スクリプト タスクの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="544bd-112">To set the default scripting language for the Script task, use the **Scripting language** option on **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="544bd-113">詳細については、「 [General Page](general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="544bd-113">For more information, see [General Page](general-page-of-integration-services-designers-options.md).</span></span>  
  
 <span data-ttu-id="544bd-114">**EntryPoint**</span><span class="sxs-lookup"><span data-stu-id="544bd-114">**EntryPoint**</span></span>  
 <span data-ttu-id="544bd-115">スクリプト タスクのコードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ランタイムが呼び出すメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="544bd-115">Specify the method that the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] runtime calls as the entry point into the code of the Script task.</span></span> <span data-ttu-id="544bd-116">指定されたメソッドは、Tools for Applications (VSTA) プロジェクトの ScriptMain クラスに存在する必要があります [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 。 scriptmain クラスは、スクリプトテンプレートによって生成される既定のクラスです。</span><span class="sxs-lookup"><span data-stu-id="544bd-116">The specified method must be in the ScriptMain class of the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) project The ScriptMain class is the default class generated by the script templates.</span></span>  
  
 <span data-ttu-id="544bd-117">VSTA プロジェクトでメソッドの名前を変更する場合は、 **EntryPoint** プロパティの値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="544bd-117">If you change the name of the method in the VSTA project, you must change the value of the **EntryPoint** property.</span></span>  
  
 <span data-ttu-id="544bd-118">**[ReadOnlyVariables]**</span><span class="sxs-lookup"><span data-stu-id="544bd-118">**ReadOnlyVariables**</span></span>  
 <span data-ttu-id="544bd-119">スクリプトで使用できる読み取り専用変数のコンマ区切りの一覧を入力するか、省略記号ボタン ([**..**.]) をクリックして、[**変数の選択**] ダイアログボックスで変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="544bd-119">Type a comma-separated list of read-only variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="544bd-120">変数名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="544bd-120">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="544bd-121">**[ReadWriteVariables]**</span><span class="sxs-lookup"><span data-stu-id="544bd-121">**ReadWriteVariables**</span></span>  
 <span data-ttu-id="544bd-122">スクリプトに使用できる読み取り/書き込み用の変数の一覧をコンマ区切りで入力するか、省略記号ボタン ( **[...]** ) をクリックして **[変数の選択]** ダイアログ ボックスで変数を選択します。</span><span class="sxs-lookup"><span data-stu-id="544bd-122">Type a comma-separated list of read/write variables that are available to the script, or click the ellipsis (**...**) button and select the variables in the **Select variables** dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="544bd-123">変数名では大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="544bd-123">Variable names are case sensitive.</span></span>  
  
 <span data-ttu-id="544bd-124">**[スクリプトの編集]**</span><span class="sxs-lookup"><span data-stu-id="544bd-124">**Edit Script**</span></span>  
 <span data-ttu-id="544bd-125">スクリプトを作成または変更できる VSTA IDE が開きます。</span><span class="sxs-lookup"><span data-stu-id="544bd-125">Opens the VSTA IDE where you can create or modify the script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544bd-126">参照</span><span class="sxs-lookup"><span data-stu-id="544bd-126">See Also</span></span>  
 <span data-ttu-id="544bd-127">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-127">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="544bd-128">[[全般] ページ](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-128">[General Page](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="544bd-129">[スクリプトタスクエディター &#40;[全般] ページ&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-129">[Script Task Editor &#40;General Page&#41;](../../2014/integration-services/script-task-editor-general-page.md) </span></span>  
 <span data-ttu-id="544bd-130">[[式] ページ](expressions/expressions-page.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-130">[Expressions Page](expressions/expressions-page.md) </span></span>  
 <span data-ttu-id="544bd-131">[スクリプトタスクの例](extending-packages-scripting-task-examples/script-task-examples.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-131">[Script Task Examples](extending-packages-scripting-task-examples/script-task-examples.md) </span></span>  
 <span data-ttu-id="544bd-132">[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="544bd-132">[Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="544bd-133">パッケージ内のユーザー定義変数のスコープの追加、削除、変更</span><span class="sxs-lookup"><span data-stu-id="544bd-133">Add, Delete, Change Scope of User-Defined Variable in a Package</span></span>](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
