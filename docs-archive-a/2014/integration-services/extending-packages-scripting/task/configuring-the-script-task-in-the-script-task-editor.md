---
title: スクリプト タスク エディターでのスクリプト タスクの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b75b4a030e6c5baa2e26c610b0e8216843c8cca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633906"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a><span data-ttu-id="effa1-102">スクリプト タスク エディターでのスクリプト タスクの構成</span><span class="sxs-lookup"><span data-stu-id="effa1-102">Configuring the Script Task in the Script Task Editor</span></span>
  <span data-ttu-id="effa1-103">スクリプト タスクにカスタム コードを記述する前に、 **[スクリプト タスク エディター]** の 3 つのページで、主要なプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="effa1-103">Before you write custom code in the Script task, you configure its principal properties in the three pages of the **Script Task Editor**.</span></span> <span data-ttu-id="effa1-104">スクリプト タスクに対して一意でない追加のタスク プロパティは、[プロパティ] ウィンドウを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="effa1-104">You can configure additional task properties that are not unique to the Script task by using the Properties window.</span></span>

> [!NOTE]
>  <span data-ttu-id="effa1-105">スクリプトをプリコンパイルするかどうかを指定できた以前のバージョンとは異なり、[!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 以降ではすべてのスクリプトがプリコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="effa1-105">Unlike earlier versions where you could indicate whether scripts were precompiled, all scripts are precompiled beginning in [!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)].</span></span>

## <a name="general-page-of-the-script-task-editor"></a><span data-ttu-id="effa1-106">[スクリプト タスク エディター] の [全般] ページ</span><span class="sxs-lookup"><span data-stu-id="effa1-106">General Page of the Script Task Editor</span></span>
 <span data-ttu-id="effa1-107">**[スクリプト タスク エディター]** の **[全般]** ページでは、スクリプト タスクに一意の名前および説明を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="effa1-107">On the **General** page of the **Script Task Editor**, you assign a unique name and a description for the Script task.</span></span>

## <a name="script-page-of-the-script-task-editor"></a><span data-ttu-id="effa1-108">[スクリプト タスク エディター] の [スクリプト] ページ</span><span class="sxs-lookup"><span data-stu-id="effa1-108">Script Page of the Script Task Editor</span></span>
 <span data-ttu-id="effa1-109">**[スクリプト タスク エディター]** の **[スクリプト]** ページには、スクリプト タスクのカスタム プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="effa1-109">The **Script** page of the **Script Task Editor** displays the custom properties of the Script task.</span></span>

### <a name="scriptlanguage-property"></a><span data-ttu-id="effa1-110">ScriptLanguage プロパティ</span><span class="sxs-lookup"><span data-stu-id="effa1-110">ScriptLanguage Property</span></span>
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="effa1-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) では、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# のプログラミング言語がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="effa1-111">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) supports the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# programming languages.</span></span> <span data-ttu-id="effa1-112">スクリプト タスクにスクリプトを作成した後で、 **[ScriptLanguage]** プロパティの値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="effa1-112">After you create a script in the Script task, you cannot change value of the **ScriptLanguage** property.</span></span>

 <span data-ttu-id="effa1-113">スクリプト タスクとスクリプト コンポーネントの既定のスクリプト言語を設定するには、**[オプション]** ダイアログ ボックスの **[全般]** ページにある **[ScriptLanguage]** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="effa1-113">To set the default script language for Script tasks and Script components, use the **ScriptLanguage** property on the **General** page of the **Options** dialog box.</span></span> <span data-ttu-id="effa1-114">詳細については、「 [General Page](../../general-page-of-integration-services-designers-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="effa1-114">For more information, see [General Page](../../general-page-of-integration-services-designers-options.md).</span></span>

### <a name="entrypoint-property"></a><span data-ttu-id="effa1-115">EntryPoint プロパティ</span><span class="sxs-lookup"><span data-stu-id="effa1-115">EntryPoint Property</span></span>
 <span data-ttu-id="effa1-116">`EntryPoint` プロパティは、スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトの `ScriptMain` クラスのメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="effa1-116">The `EntryPoint` property specifies the method on the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="effa1-117">`ScriptMain` クラスは、スクリプト テンプレートによって生成される既定のクラスです。</span><span class="sxs-lookup"><span data-stu-id="effa1-117">The `ScriptMain` class is the default class generated by the script templates.</span></span>

 <span data-ttu-id="effa1-118">VSTA プロジェクトでメソッドの名前を変更する場合は、`EntryPoint` プロパティの値を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="effa1-118">If you change the name of the method in the VSTA project, you must change the value of the `EntryPoint` property.</span></span>

### <a name="readonlyvariables-and-readwritevariables-properties"></a><span data-ttu-id="effa1-119">ReadOnlyVariables プロパティおよび ReadWriteVariables プロパティ</span><span class="sxs-lookup"><span data-stu-id="effa1-119">ReadOnlyVariables and ReadWriteVariables Properties</span></span>
 <span data-ttu-id="effa1-120">既存の変数をコンマ区切りリストとして、これらのプロパティの値に入力すると、スクリプト タスクのコード内で、その変数に読み取り専用アクセスまたは読み取り/書き込みアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="effa1-120">You can enter comma-delimited lists of existing variables as the values of these properties to make the variables available for read-only or read/write access within the Script task code.</span></span> <span data-ttu-id="effa1-121">どちらの種類の変数にも、`Dts` オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを介して、コード内でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="effa1-121">Variables of both types are accessed in code through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> property of the `Dts` object.</span></span> <span data-ttu-id="effa1-122">詳細については、「 [スクリプト タスクでの変数の使用](../../extending-packages-scripting/task/using-variables-in-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="effa1-122">For more information, see [Using Variables in the Script Task](../../extending-packages-scripting/task/using-variables-in-the-script-task.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="effa1-123">変数名の大文字と小文字は区別されます。</span><span class="sxs-lookup"><span data-stu-id="effa1-123">Variable names are case-sensitive.</span></span>

 <span data-ttu-id="effa1-124">変数を選択するには、プロパティ フィールドの横にある参照ボタン **[...]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="effa1-124">To select the variables, click the ellipsis (**...**) button next to the property field.</span></span> <span data-ttu-id="effa1-125">詳細については、「[[変数の選択] ページ](../../control-flow/select-variables-page.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="effa1-125">For more information, see [Select Variables Page](../../control-flow/select-variables-page.md).</span></span>

### <a name="edit-script-button"></a><span data-ttu-id="effa1-126">[スクリプトの編集] ボタン</span><span class="sxs-lookup"><span data-stu-id="effa1-126">Edit Script Button</span></span>
 <span data-ttu-id="effa1-127">**[スクリプトの編集]** ボタンをクリックすると VSTA 開発環境が起動し、カスタム スクリプトを記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="effa1-127">The **Edit Script** button launches the VSTA development environment in which you write your custom script.</span></span> <span data-ttu-id="effa1-128">詳細については、「[スクリプト タスクのコーディングおよびデバッグ](coding-and-debugging-the-script-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="effa1-128">For more information, see [Coding and Debugging the Script Task](coding-and-debugging-the-script-task.md).</span></span>

## <a name="expressions-page-of-the-script-task-editor"></a><span data-ttu-id="effa1-129">[スクリプト タスク エディター] の [式] ページ</span><span class="sxs-lookup"><span data-stu-id="effa1-129">Expressions Page of the Script Task Editor</span></span>
 <span data-ttu-id="effa1-130">**[スクリプト タスク エディター]** の **[式]** ページでは、式を使用して、上に挙げたスクリプト タスクのプロパティ、およびそれ以外の多くのプロパティに値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="effa1-130">On the **Expressions** page of the **Script Task Editor**, you can use expressions to provide values for the properties of the Script task listed above and for many other task properties.</span></span> <span data-ttu-id="effa1-131">詳細については、「 [Integration Services (SSIS) 式](../../expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="effa1-131">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md).</span></span>

<span data-ttu-id="effa1-132">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="effa1-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="effa1-133">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="effa1-133">For the latest downloads, articles, samples, and videos from [!INCLUDE[msCoName](../../../includes/msconame-md.md)], as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="effa1-134">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="effa1-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="effa1-135">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="effa1-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="effa1-136">参照</span><span class="sxs-lookup"><span data-stu-id="effa1-136">See Also</span></span>
 [<span data-ttu-id="effa1-137">スクリプト タスクのコーディングおよびデバッグ</span><span class="sxs-lookup"><span data-stu-id="effa1-137">Coding and Debugging the Script Task</span></span>](coding-and-debugging-the-script-task.md)


