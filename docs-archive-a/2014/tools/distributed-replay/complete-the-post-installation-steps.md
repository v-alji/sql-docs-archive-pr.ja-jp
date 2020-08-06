---
title: インストール後の手順を実行します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 0a788a2a-9b4f-4bfc-b1b5-83eeb1ea9ab2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1e9aae3dccaa409bcebc473213286f3edf19e7f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641919"
---
# <a name="complete-the-post-installation-steps"></a><span data-ttu-id="bba7b-102">インストール後の手順の実行</span><span class="sxs-lookup"><span data-stu-id="bba7b-102">Complete the Post-Installation Steps</span></span>
  <span data-ttu-id="bba7b-103">分散再生をインストールした後、分散再生コントローラー サービスおよび分散再生クライアント サービスのアカウントを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bba7b-103">After you install Distributed Replay you must modify the Distributed Replay controller and client services accounts.</span></span>  
  
### <a name="to-complete-the-post-installation-steps"></a><span data-ttu-id="bba7b-104">インストール後の手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="bba7b-104">To complete the post-installation steps</span></span>  
  
1.  <span data-ttu-id="bba7b-105">**ファイアウォール規則を作成する**:コントローラー コンピューターとクライアント コンピューターで、対応するサービスのファイアウォール経由の受信トラフィックを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bba7b-105">**Create firewall rules**: On the controller and client computers, you must allow inbound traffic through the firewall for the corresponding service.</span></span> <span data-ttu-id="bba7b-106">インストール フォルダーに配置されているサービス実行可能ファイルのファイアウォール ルールを指定します。</span><span class="sxs-lookup"><span data-stu-id="bba7b-106">Specify the firewall rules for the service executables, located in the installation folders.</span></span>  
  
    1.  <span data-ttu-id="bba7b-107">コントローラー サービスの場合は、インストール フォルダーにある **DReplayController.exe**のルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="bba7b-107">For the controller service, create a rule for **DReplayController.exe**, located in the installation folder.</span></span> <span data-ttu-id="bba7b-108">たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。</span><span class="sxs-lookup"><span data-stu-id="bba7b-108">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay controller" dir=in program="%InstallPath%\DReplayController\DReplayController.exe" action=allow`  
  
    2.  <span data-ttu-id="bba7b-109">クライアント サービスの場合は、クライアント コンピューターごとに、インストール フォルダーにある **DReplayClient.exe**のルールを作成します。</span><span class="sxs-lookup"><span data-stu-id="bba7b-109">For the client service, on each client computer, create a rule for **DReplayClient.exe**, located in the installation folder.</span></span> <span data-ttu-id="bba7b-110">たとえば、次のコマンドを実行すると、このルールが有効になります ( `%InstallPath%` はサービスのインストール フォルダーです)。</span><span class="sxs-lookup"><span data-stu-id="bba7b-110">For example, the following command enables this rule, where `%InstallPath%` is the installation folder of the service:</span></span>  
  
         `netsh advfirewall firewall add rule name="allow dreplay client" dir=in program="%InstallPath%\DReplayClient\DReplayClient.exe" action=allow`  
  
2.  <span data-ttu-id="bba7b-111">**ターゲット サーバーで各クライアントの権限を与える**:クライアント コンピューターへのクライアント サービスのインストールが完了したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のターゲット インスタンスの sysadmin ロールにクライアント サービス アカウントを手動で追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bba7b-111">**Grant each client permissions on the target server**: After you have completed installing the client service on the client computers, you must manually add the client service accounts to the sysadmin role on the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bba7b-112">.NET Framework のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="bba7b-112">.NET Framework Security</span></span>  
 <span data-ttu-id="bba7b-113">分散再生の機能をインストールするには、管理権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="bba7b-113">You must have administrative permissions in order to install any of the Distributed Replay features.</span></span> <span data-ttu-id="bba7b-114">sysadmin 権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのみが、テスト サーバーの sysadmin サーバー ロールにクライアント サービス アカウントを追加できます。</span><span class="sxs-lookup"><span data-stu-id="bba7b-114">Only a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login having sysadmin permissions can add the client service accounts to the sysadmin server role of the test server.</span></span> <span data-ttu-id="bba7b-115">Distributed Replay のセキュリティ上の考慮事項の詳細については、「 [Distributed Replay のセキュリティ](distributed-replay-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bba7b-115">For more information about Distributed Replay security considerations, see [Distributed Replay Security](distributed-replay-security.md).</span></span>  
  
  
