---
title: '[パッケージの選択] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.selectapackage.f1
helpviewer_keywords:
- Select a Package dialog box
ms.assetid: 92b47a2b-21b5-460a-885d-6cc4bb567249
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b35276791b004a011a1c2656057046be05ed6770
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631185"
---
# <a name="select-a-package"></a><span data-ttu-id="072cd-102">[パッケージの選択]</span><span class="sxs-lookup"><span data-stu-id="072cd-102">Select a Package</span></span>
  <span data-ttu-id="072cd-103">**[パッケージの選択]** ダイアログ ボックスを使用すると、メッセージ キュー タスクで受信されるメッセージの送信元パッケージを指定できます。</span><span class="sxs-lookup"><span data-stu-id="072cd-103">Use the **Select a Package** dialog box to specify the package from which the Message Queue task can receive messages.</span></span>  
  
## <a name="static-options"></a><span data-ttu-id="072cd-104">静的オプション</span><span class="sxs-lookup"><span data-stu-id="072cd-104">Static Options</span></span>  
 <span data-ttu-id="072cd-105">**Location**</span><span class="sxs-lookup"><span data-stu-id="072cd-105">**Location**</span></span>  
 <span data-ttu-id="072cd-106">パッケージの場所を特定します。</span><span class="sxs-lookup"><span data-stu-id="072cd-106">Specify the location of the package.</span></span> <span data-ttu-id="072cd-107">このプロパティのオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="072cd-107">This property has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="072cd-108">値</span><span class="sxs-lookup"><span data-stu-id="072cd-108">Value</span></span>|<span data-ttu-id="072cd-109">説明</span><span class="sxs-lookup"><span data-stu-id="072cd-109">Description</span></span>|  
|-----------|-----------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<span data-ttu-id="072cd-110">場所を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="072cd-110">Set the location to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="072cd-111">この値を選択すると、動的オプションの [パッケージ名]、 **[サーバー]** 、 **[Windows 認証を使用する]** 、 **[SQL Server 認証を使用する]** 、 **[ユーザー名]** 、および **[パスワード]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="072cd-111">Selecting this value displays the dynamic options, **Server**, **Use Windows Authentication**, **Use SQL Server Authentication**, **User name**, and **Password**.</span></span>|  
|<span data-ttu-id="072cd-112">[DTSX ファイル]</span><span class="sxs-lookup"><span data-stu-id="072cd-112">DTSX file</span></span>|<span data-ttu-id="072cd-113">DTSX ファイルの場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="072cd-113">Set the location to a DTSX file.</span></span> <span data-ttu-id="072cd-114">この値を選択すると、動的オプションの **[ファイル名]** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="072cd-114">Selecting this value displays the dynamic option, **File name**.</span></span>|  
  
## <a name="location-dynamic-options"></a><span data-ttu-id="072cd-115">[Location] の動的オプション</span><span class="sxs-lookup"><span data-stu-id="072cd-115">Location Dynamic Options</span></span>  
  
### <a name="location--sql-server"></a><span data-ttu-id="072cd-116">Location = SQL Server</span><span class="sxs-lookup"><span data-stu-id="072cd-116">Location = SQL Server</span></span>  
 <span data-ttu-id="072cd-117">**パッケージ名**</span><span class="sxs-lookup"><span data-stu-id="072cd-117">**Package name**</span></span>  
 <span data-ttu-id="072cd-118">指定したサーバーに格納されているパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="072cd-118">Select a package that is stored on the specified server.</span></span>  
  
 <span data-ttu-id="072cd-119">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="072cd-119">**Server**</span></span>  
 <span data-ttu-id="072cd-120">サーバーの名前を入力するか、サーバーを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="072cd-120">Provide a server name or select a server from the list.</span></span>  
  
 <span data-ttu-id="072cd-121">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="072cd-121">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="072cd-122">Windows 認証を使用する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="072cd-122">Click to use Windows Authentication.</span></span>  
  
 <span data-ttu-id="072cd-123">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="072cd-123">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="072cd-124">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="072cd-124">Click to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
 <span data-ttu-id="072cd-125">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="072cd-125">**User name**</span></span>  
 <span data-ttu-id="072cd-126">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、サーバーにログオンするときに使用するユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="072cd-126">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a user name to use when logging on to the server.</span></span>  
  
 <span data-ttu-id="072cd-127">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="072cd-127">**Password**</span></span>  
 <span data-ttu-id="072cd-128">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="072cd-128">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, provide a password.</span></span>  
  
### <a name="location--dtsx-file"></a><span data-ttu-id="072cd-129">[場所] = [DTSX ファイル]</span><span class="sxs-lookup"><span data-stu-id="072cd-129">Location = DTSX file</span></span>  
 <span data-ttu-id="072cd-130">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="072cd-130">**File name**</span></span>  
 <span data-ttu-id="072cd-131">パッケージのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてパッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="072cd-131">Provide the path of a package or click the browse button **(...)** and locate the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072cd-132">参照</span><span class="sxs-lookup"><span data-stu-id="072cd-132">See Also</span></span>  
 [<span data-ttu-id="072cd-133">メッセージ キュー タスク</span><span class="sxs-lookup"><span data-stu-id="072cd-133">Message Queue Task</span></span>](message-queue-task.md)  
  
  
