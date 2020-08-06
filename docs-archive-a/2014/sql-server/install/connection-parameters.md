---
title: 接続パラメーター |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 27eb69dfd2c41710a47861e0992486267f692a3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634241"
---
# <a name="connection-parameters"></a><span data-ttu-id="5d29f-102">接続パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d29f-102">Connection Parameters</span></span>
  <span data-ttu-id="5d29f-103">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]など、特定の種類のサーバーを分析するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の特定のインスタンスを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d29f-103">To analyze certain server types, such as the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], you must select a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="5d29f-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のインスタンスは自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="5d29f-104">The default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is automatically selected.</span></span> <span data-ttu-id="5d29f-105">この選択は変更できますが、アップグレード アドバイザーによる分析用に選択できるのは一度に 1 つのインスタンスだけです。</span><span class="sxs-lookup"><span data-stu-id="5d29f-105">You can change this selection, but you can select only one instance at a time for analysis by Upgrade Advisor.</span></span> <span data-ttu-id="5d29f-106">認証が必要なサーバーを選択した場合は、認証モードと資格情報を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d29f-106">If you have included a server type that requires authentication, you must enter the authentication mode and credentials.</span></span>  
  
## <a name="options"></a><span data-ttu-id="5d29f-107">Options</span><span class="sxs-lookup"><span data-stu-id="5d29f-107">Options</span></span>  
 <span data-ttu-id="5d29f-108">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="5d29f-108">**Server name**</span></span>  
 <span data-ttu-id="5d29f-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネント ペインに入力したコンピューター名が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="5d29f-109">Pre-populated with the computer name that you entered in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Components pane.</span></span>  
  
 <span data-ttu-id="5d29f-110">**インスタンス名**</span><span class="sxs-lookup"><span data-stu-id="5d29f-110">**Instance name**</span></span>  
 <span data-ttu-id="5d29f-111">コンピューターで使用可能な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスから選択します。</span><span class="sxs-lookup"><span data-stu-id="5d29f-111">Select from the instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that are available on the computer.</span></span> <span data-ttu-id="5d29f-112">インスタンスの一覧が表示されない場合は、MSSQLSERVER を使用して既定のインスタンスをスキャンします。</span><span class="sxs-lookup"><span data-stu-id="5d29f-112">If you do not see a list of instances, use MSSQLSERVER to scan the default instance.</span></span> <span data-ttu-id="5d29f-113">これは、特にリモート コンピューターに関連します。</span><span class="sxs-lookup"><span data-stu-id="5d29f-113">This is especially relevant for remote computers.</span></span> <span data-ttu-id="5d29f-114">「default」と入力して、既定のインスタンスをスキャンすることもできます。</span><span class="sxs-lookup"><span data-stu-id="5d29f-114">You can also use the word "default" to scan the default instance.</span></span>  
  
 <span data-ttu-id="5d29f-115">**認証**</span><span class="sxs-lookup"><span data-stu-id="5d29f-115">**Authentication**</span></span>  
 <span data-ttu-id="5d29f-116">このコンピューターで使用できる認証モードの一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="5d29f-116">Select from the list of available authentication modes on this computer.</span></span> <span data-ttu-id="5d29f-117">既定の認証モードは Windows 認証です。</span><span class="sxs-lookup"><span data-stu-id="5d29f-117">By default, the authentication mode is Windows Authentication.</span></span>  
  
 <span data-ttu-id="5d29f-118">**ユーザー名**</span><span class="sxs-lookup"><span data-stu-id="5d29f-118">**User name**</span></span>  
 <span data-ttu-id="5d29f-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用する場合は、このボックスにユーザー名を入力します。</span><span class="sxs-lookup"><span data-stu-id="5d29f-119">If using [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication, enter a user name in the box.</span></span> <span data-ttu-id="5d29f-120">ここには、コンピューターの管理者の資格情報を持っているユーザー名を入力することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5d29f-120">We recommend that the user name have administrative credentials on the computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5d29f-121">[Windows 認証] を選択した場合は、現在ログオンしているユーザーのユーザー名が [**ユーザー名**] ボックスに入力されます。</span><span class="sxs-lookup"><span data-stu-id="5d29f-121">If you select Windows Authentication, the user name of the currently logged-on user is populated in the **User name** text box.</span></span>  
  
 <span data-ttu-id="5d29f-122">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="5d29f-122">**Password**</span></span>  
 <span data-ttu-id="5d29f-123">指定したユーザーのパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="5d29f-123">Enter the password for the specified user.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d29f-124">参照</span><span class="sxs-lookup"><span data-stu-id="5d29f-124">See Also</span></span>  
 <span data-ttu-id="5d29f-125">[アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="5d29f-125">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="5d29f-126">アップグレード アドバイザーのユーザー インターフェイス リファレンス</span><span class="sxs-lookup"><span data-stu-id="5d29f-126">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
