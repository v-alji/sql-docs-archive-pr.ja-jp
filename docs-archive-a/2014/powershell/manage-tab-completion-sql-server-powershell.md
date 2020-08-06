---
title: タブ補完の管理 (SQL Server PowerShell) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: 6296848a-890f-4ad3-8d9f-92ed6a79aa00
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72bcf96245c536d6ea444bc1d7964b7579e793c8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645700"
---
# <a name="manage-tab-completion-sql-server-powershell"></a><span data-ttu-id="01138-102">タブ補完の管理 (SQL Server PowerShell)</span><span class="sxs-lookup"><span data-stu-id="01138-102">Manage Tab Completion (SQL Server PowerShell)</span></span>
  <span data-ttu-id="01138-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell スナップインには、Windows PowerShell のタブ補完を制御するための 3 つの変数 (`$SqlServerMaximumTabCompletion`、`$SqlServerMaximumChildItems`、および `$SqlServerIncludeSystemObjects`) が追加されました。</span><span class="sxs-lookup"><span data-stu-id="01138-103">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell snap-ins introduce three variables (`$SqlServerMaximumTabCompletion`, `$SqlServerMaximumChildItems`, and `$SqlServerIncludeSystemObjects`) to control Windows PowerShell tab completion.</span></span> <span data-ttu-id="01138-104">入力された文字列で名前が始まるアイテムの一覧を返すタブ補完によって、入力の手間を削減することができます。</span><span class="sxs-lookup"><span data-stu-id="01138-104">Tab completion reduces the amount of typing you must do by returning tables of items whose names start with the string you are typing.</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="01138-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="01138-105">Before You Begin</span></span>  
 <span data-ttu-id="01138-106">Windows PowerShell のタブ補完機能では、パスやコマンドレット名の一部を入力して Tab キーを押すと、既に入力した部分に一致する名前のアイテムの一覧を取得できます。</span><span class="sxs-lookup"><span data-stu-id="01138-106">With Windows PowerShell tab-completion, when you have typed part of a path or cmdlet name, you can hit the Tab key to get a list of the items whose names match what you have already typed.</span></span> <span data-ttu-id="01138-107">名前の残りの部分を入力しなくても、その一覧からアイテムを選択できます。</span><span class="sxs-lookup"><span data-stu-id="01138-107">You can then select the item you want from the list without having to type the rest of the name.</span></span>  
  
 <span data-ttu-id="01138-108">多数のオブジェクトを含むデータベースで作業する場合、タブ補完の一覧が非常に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01138-108">If you are working in a database that has a lot of objects, the tab-completion lists can become very large.</span></span> <span data-ttu-id="01138-109">また、ビューなどの一部の種類の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オブジェクトには、多数のシステム オブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="01138-109">Some [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] object types, such as views, also have large numbers of system objects.</span></span>  
  
 <span data-ttu-id="01138-110">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] スナップインでは、タブ補完および **Get-ChildItem**で表示される情報の量を制御するために使用できる 3 つのシステム変数が導入されています。</span><span class="sxs-lookup"><span data-stu-id="01138-110">The [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] snap-ins introduces three system variables that you can use to control the amount of information presented by tab-completion and **Get-ChildItem**.</span></span>  
  
 <span data-ttu-id="01138-111">**$SqlServerMaximumTabCompletion =** *n*</span><span class="sxs-lookup"><span data-stu-id="01138-111">**$SqlServerMaximumTabCompletion =** *n*</span></span>  
 <span data-ttu-id="01138-112">タブ補完の一覧に含めるオブジェクトの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="01138-112">Specifies the maximum number of objects to include in a tab-completion list.</span></span> <span data-ttu-id="01138-113">*n* を超える数のオブジェクトが含まれるパス ノードで Tab キーを押した場合、タブ補完の一覧が *n*件までで切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="01138-113">If you select Tab at a path node having more than *n* objects, the tab-completion list is truncated at *n*.</span></span> <span data-ttu-id="01138-114">*n* は整数です。</span><span class="sxs-lookup"><span data-stu-id="01138-114">*n* is an integer.</span></span> <span data-ttu-id="01138-115">既定の設定は 0 で、これは一覧表示されるオブジェクトの数に制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="01138-115">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="01138-116">**$SqlServerMaximumChildItems =** *n*</span><span class="sxs-lookup"><span data-stu-id="01138-116">**$SqlServerMaximumChildItems =** *n*</span></span>  
 <span data-ttu-id="01138-117">**Get-ChildItem**で表示されるオブジェクトの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="01138-117">Specifies the maximum number of objects displayed by **Get-ChildItem**.</span></span> <span data-ttu-id="01138-118">**n** を超える数のオブジェクトが含まれるパス ノードで *Get-ChildItem* を実行した場合、一覧が *n*件までで切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="01138-118">If **Get-ChildItem** is run at a path node having more than *n* objects, the list is truncated at *n*.</span></span> <span data-ttu-id="01138-119">*n* は整数です。</span><span class="sxs-lookup"><span data-stu-id="01138-119">*n* is an integer.</span></span> <span data-ttu-id="01138-120">既定の設定は 0 で、これは一覧表示されるオブジェクトの数に制限がないことを示します。</span><span class="sxs-lookup"><span data-stu-id="01138-120">0 is the default setting, and means there is no limit to the number of objects listed.</span></span>  
  
 <span data-ttu-id="01138-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span><span class="sxs-lookup"><span data-stu-id="01138-121">**$SqlServerIncludeSystemObjects =** { **$True** | **$False** }</span></span>  
 <span data-ttu-id="01138-122">**$True**の場合、タブ補完と **Get-ChildItem**でシステム オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01138-122">If **$True**, system objects are displayed by tab-completion and **Get-ChildItem**.</span></span> <span data-ttu-id="01138-123">**$False**の場合、システム オブジェクトは表示されません。</span><span class="sxs-lookup"><span data-stu-id="01138-123">If **$False**, no system objects are displayed.</span></span> <span data-ttu-id="01138-124">既定の設定は **$False**です。</span><span class="sxs-lookup"><span data-stu-id="01138-124">The default setting is **$False**.</span></span>  
  
## <a name="set-the-sql-server-tab-completion-variables"></a><span data-ttu-id="01138-125">SQL Server のタブ補完変数の設定</span><span class="sxs-lookup"><span data-stu-id="01138-125">Set the SQL Server Tab Completion Variables</span></span>  
 <span data-ttu-id="01138-126">既定値から変更する場合は、その対象となるすべての変数について、新しい値を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01138-126">For any of the variables you want to change from the default value, set the variable to the new value.</span></span>  
  
### <a name="example-powershell"></a><span data-ttu-id="01138-127">例 (PowerShell)</span><span class="sxs-lookup"><span data-stu-id="01138-127">Example (PowerShell)</span></span>  
 <span data-ttu-id="01138-128">次の例では、3 つすべての変数を設定し、設定を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="01138-128">The following example sets all three variables and lists their settings:</span></span>  
  
```powershell
$SqlServerMaximumTabCompletion = 20  
$SqlServerMaximumChildItems = 10  
$SqlServerIncludeSystemObjects = $False  
dir variable:sqlserver*  
```  
  
## <a name="see-also"></a><span data-ttu-id="01138-129">参照</span><span class="sxs-lookup"><span data-stu-id="01138-129">See Also</span></span>  
 [<span data-ttu-id="01138-130">SQL Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="01138-130">SQL Server PowerShell</span></span>](sql-server-powershell.md)  
