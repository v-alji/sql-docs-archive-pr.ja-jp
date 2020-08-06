---
title: WMI エラー 0x8007052f | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d6e857e0ccaad9b6f34bbdc9b88aea2e6d7291d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743117"
---
# <a name="wmi-error-0x8007052f"></a><span data-ttu-id="6c649-102">WMI エラー 0x8007052f</span><span class="sxs-lookup"><span data-stu-id="6c649-102">WMI Error 0x8007052f</span></span>
    
## <a name="details"></a><span data-ttu-id="6c649-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6c649-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6c649-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6c649-104">Product Name</span></span>|<span data-ttu-id="6c649-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6c649-105">SQL Server</span></span>|  
|<span data-ttu-id="6c649-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6c649-106">Event ID</span></span>|<span data-ttu-id="6c649-107">0x8007052f</span><span class="sxs-lookup"><span data-stu-id="6c649-107">0x8007052f</span></span>|  
|<span data-ttu-id="6c649-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6c649-108">Event Source</span></span>|<span data-ttu-id="6c649-109">WMI プロバイダー エラー</span><span class="sxs-lookup"><span data-stu-id="6c649-109">WMI Provider Error</span></span>|  
|<span data-ttu-id="6c649-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6c649-110">Component</span></span>|<span data-ttu-id="6c649-111">SQL Server 構成マネージャー</span><span class="sxs-lookup"><span data-stu-id="6c649-111">SQL Server Configuration Manager</span></span>|  
|<span data-ttu-id="6c649-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6c649-112">Symbolic Name</span></span>|<span data-ttu-id="6c649-113">NA</span><span class="sxs-lookup"><span data-stu-id="6c649-113">NA</span></span>|  
|<span data-ttu-id="6c649-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6c649-114">Message Text</span></span>|<span data-ttu-id="6c649-115">ログオン失敗: ユーザー アカウントの制限。</span><span class="sxs-lookup"><span data-stu-id="6c649-115">Logon failure: user account restriction.</span></span> <span data-ttu-id="6c649-116">考えられる原因として、空のパスワードが許可されていない、ログオン時間制限、またはポリシーによる制限が適用されたことなどが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="6c649-116">Possible reasons are blank passwords not allowed, login hour restrictions, or a policy restriction has been enforced.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6c649-117">説明</span><span class="sxs-lookup"><span data-stu-id="6c649-117">Explanation</span></span>  
 <span data-ttu-id="6c649-118">このエラーは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が Windows Server クラスターまたは Windows Server ドメイン コントローラー上で実行されているときに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用してビルトイン アカウント (Network Service、Local Service、または Local System) に切り替えると発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6c649-118">This error can occur when using [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager to switch to the built-in accounts (Network Service, Local Service, or Local System) when [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is running on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="6c649-119">Windows Server クラスターまたは Windows Server ドメイン コントローラー上では、ビルトイン アカウントでサービスを実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="6c649-119">Do not run services under built-in accounts on a Windows Server Cluster or Windows Server Domain Controller.</span></span> <span data-ttu-id="6c649-120">サービス アカウントに関する推奨事項については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c649-120">For recommendations on service accounts, see the topic Setting Up Windows Service Accounts in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6c649-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6c649-121">User Action</span></span>  
 <span data-ttu-id="6c649-122">ドメイン アカウントを使用するように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を構成します。</span><span class="sxs-lookup"><span data-stu-id="6c649-122">Configure [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to use a domain account.</span></span>  
  
  
