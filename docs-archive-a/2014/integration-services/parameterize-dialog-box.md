---
title: パラメーター化ダイアログボックス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.parameter.f1
ms.assetid: fac02b6d-d247-447a-8940-e8700c7ac350
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db19844132402740aec092d6e88f3c9e3864d58
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641045"
---
# <a name="parameterize-dialog-box"></a><span data-ttu-id="90972-102">Parameterize Dialog Box</span><span class="sxs-lookup"><span data-stu-id="90972-102">Parameterize Dialog Box</span></span>
  <span data-ttu-id="90972-103">**[パラメーター化]** ダイアログ ボックスでは、新規または既存のパラメーターをタスクのプロパティと関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="90972-103">The **Parameterize** dialog box enables you to associate a new or an existing parameter with a property of a task.</span></span> <span data-ttu-id="90972-104">このダイアログ ボックスを開くには、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでタスクまたは [制御フロー] タブを右クリックし、**[パラメーター化]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="90972-104">You open the dialog box by right-clicking a task or the Control Flow tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and then by clicking **Parameterize**.</span></span> <span data-ttu-id="90972-105">次の一覧では、このダイアログ ボックスの UI 要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90972-105">The following list describes UI elements in the dialog box.</span></span> <span data-ttu-id="90972-106">パラメーターについて詳しくは、「[Integration Services &#40;SSIS&#41; パラメーター](integration-services-ssis-package-and-project-parameters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="90972-106">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="90972-107">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="90972-107">UI element list</span></span>  
 <span data-ttu-id="90972-108">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="90972-108">**Property**</span></span>  
 <span data-ttu-id="90972-109">パラメーターと関連付けるタスクのプロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="90972-109">Select the property of the task that you want to associate with a parameter.</span></span> <span data-ttu-id="90972-110">この一覧には、パラメーター化できるすべてのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="90972-110">This list is populated with all the properties that can be parameterized.</span></span>  
  
 <span data-ttu-id="90972-111">**既存のパラメーターを使用する**</span><span class="sxs-lookup"><span data-stu-id="90972-111">**Use existing parameter**</span></span>  
 <span data-ttu-id="90972-112">タスクのプロパティを既存のパラメーターと関連付けるには、このオプションを選択し、ドロップダウン リストからパラメーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="90972-112">Select this option to associate the property of task with an existing parameter and then select the parameter from drop-down list.</span></span>  
  
 <span data-ttu-id="90972-113">**パラメーターを使用しない**</span><span class="sxs-lookup"><span data-stu-id="90972-113">**Do not use parameter**</span></span>  
 <span data-ttu-id="90972-114">パラメーターへの参照を削除するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="90972-114">Select this option to remove a reference to a parameter.</span></span> <span data-ttu-id="90972-115">パラメーターは削除されません。</span><span class="sxs-lookup"><span data-stu-id="90972-115">The parameter is not deleted.</span></span>  
  
 <span data-ttu-id="90972-116">**新しいパラメーターを作成する**</span><span class="sxs-lookup"><span data-stu-id="90972-116">**Create new parameter**</span></span>  
 <span data-ttu-id="90972-117">タスクのプロパティと関連付ける新しいパラメーターを作成するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="90972-117">Select this option to create a new parameter that you want to associate with the property of the task.</span></span>  
  
 <span data-ttu-id="90972-118">**名前**</span><span class="sxs-lookup"><span data-stu-id="90972-118">**Name**</span></span>  
 <span data-ttu-id="90972-119">作成するパラメーターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-119">Specify the name of the parameter you want to create.</span></span>  
  
 <span data-ttu-id="90972-120">**説明**</span><span class="sxs-lookup"><span data-stu-id="90972-120">**Description**</span></span>  
 <span data-ttu-id="90972-121">パラメーターの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-121">Specify the description for parameter.</span></span>  
  
 <span data-ttu-id="90972-122">**Value**</span><span class="sxs-lookup"><span data-stu-id="90972-122">**Value**</span></span>  
 <span data-ttu-id="90972-123">パラメーターの既定値を指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-123">Specify the default value for the parameter.</span></span> <span data-ttu-id="90972-124">これは設計上の既定値とも呼ばれ、後で配置時にオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="90972-124">This is also known as the design default, which can be overridden later at the deployment time.</span></span>  
  
 <span data-ttu-id="90972-125">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="90972-125">**Scope**</span></span>  
 <span data-ttu-id="90972-126">パラメーターのスコープとして、**[プロジェクト]** または **[パッケージ]** オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-126">Specify the scope of the parameter by selecting either **Project** or **Package** option.</span></span> <span data-ttu-id="90972-127">プロジェクト パラメーターは、プロジェクトが受け取る外部入力をプロジェクト内の 1 つまたは複数のパッケージに指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="90972-127">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="90972-128">パッケージ パラメーターを使用すると、パッケージを編集したり再配置したりせずにパッケージ実行を変更できます。</span><span class="sxs-lookup"><span data-stu-id="90972-128">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span>  
  
 <span data-ttu-id="90972-129">**区別**</span><span class="sxs-lookup"><span data-stu-id="90972-129">**Sensitive**</span></span>  
 <span data-ttu-id="90972-130">チェック ボックスをオンまたはオフにして、パラメーターが機密かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-130">Specify whether the parameter is a sensitive by checking or clearing the check box.</span></span> <span data-ttu-id="90972-131">機密性の高いパラメーター値はカタログ内で暗号化され、Transact-SQL または SQL Server Management Studio で表示する際は NULL 値として表示されます。</span><span class="sxs-lookup"><span data-stu-id="90972-131">Sensitive parameter values are encrypted in the catalog and appear as a NULL value when viewed with Transact-SQL or SQL Server Management Studio.</span></span>  
  
 <span data-ttu-id="90972-132">**必須**</span><span class="sxs-lookup"><span data-stu-id="90972-132">**Required**</span></span>  
 <span data-ttu-id="90972-133">パッケージを実行する前に、設計上の既定値以外の値をパラメーターに設定する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="90972-133">Specify whether the parameter requires that a value, other than the design default, is specified before the package can execute.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="90972-134">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="90972-134">UI element list</span></span>  
  
