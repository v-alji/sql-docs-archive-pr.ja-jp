---
title: '[サブスクライバーのプロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.subscribers.f1
helpviewer_keywords:
- Subscriber Properties dialog box
ms.assetid: 32aa0347-64e4-4aa4-ac57-6bd3e5d52070
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81ab9cf5f277ccfe1044e5a7083f019db9d843ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740805"
---
# <a name="subscriber-properties"></a><span data-ttu-id="bcda3-102">[サブスクライバーのプロパティ]</span><span class="sxs-lookup"><span data-stu-id="bcda3-102">Subscriber Properties</span></span>
  <span data-ttu-id="bcda3-103">**[サブスクライバーのプロパティ]** ダイアログ ボックスには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] より前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] を実行しているサブスクライバーに関連する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcda3-103">The **Subscriber Properties** dialog box contains information relevant to Subscribers running versions of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="bcda3-104">オプション</span><span class="sxs-lookup"><span data-stu-id="bcda3-104">Options</span></span>  
 <span data-ttu-id="bcda3-105">**[サブスクライバーへのエージェント接続]**</span><span class="sxs-lookup"><span data-stu-id="bcda3-105">**Agent Connection to the Subscriber**</span></span>  
 <span data-ttu-id="bcda3-106">ディストリビューターからサブスクライバーに、ディストリビューション エージェントとマージ エージェントを接続する際のコンテキストです。これは [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]より前のバージョンにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="bcda3-106">The context under which the Distribution Agent and Merge Agent connect from the Distributor to the Subscriber This applies only to versions before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].</span></span>  
  
 <span data-ttu-id="bcda3-107">**[エージェント プロセス アカウントを借用する]** を選択して、ディストリビューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのアカウントのコンテキストを使用してサブスクライバーへの接続を作成するか、 **[SQL Server 認証]** を指定して **[ログイン]** および **[パスワード]** の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="bcda3-107">Select **Impersonate agent process account** to make connections to the Subscriber using the context of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent account at the Distributor, or specify **SQL Server Authentication**, and then enter a value for **Login** and **Password**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="bcda3-108">では、 **[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bcda3-108">recommends that you select **Impersonate agent process account**.</span></span>  
  
 <span data-ttu-id="bcda3-109">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、サブスクリプションの新規作成ウィザードで各サブスクリプションについて接続情報を指定します。接続情報の変更は **[サブスクリプションのプロパティ]** ダイアログ ボックスで行います。</span><span class="sxs-lookup"><span data-stu-id="bcda3-109">For [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, connection information is specified for each subscription in the New Subscription Wizard and can be changed in the **Subscription Properties** dialog box.</span></span>  
  
 <span data-ttu-id="bcda3-110">**[既定のエージェントのスケジュール]**</span><span class="sxs-lookup"><span data-stu-id="bcda3-110">**Default Agent Schedules**</span></span>  
 <span data-ttu-id="bcda3-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]を実行しているサブスクライバーでは、サブスクリプションの新規作成ウィザードで既定のスケジュールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bcda3-111">The default schedule used in the New Subscription Wizard for Subscribers running versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].</span></span>  
  
 <span data-ttu-id="bcda3-112">**その他**</span><span class="sxs-lookup"><span data-stu-id="bcda3-112">**Miscellaneous**</span></span>  
 <span data-ttu-id="bcda3-113">サブスクライバーとサブスクライバーの種類に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bcda3-113">Includes information on the Subscriber and Subscriber type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcda3-114">参照</span><span class="sxs-lookup"><span data-stu-id="bcda3-114">See Also</span></span>  
 [<span data-ttu-id="bcda3-115">ディストリビューターとパブリッシャーのプロパティの表示および変更</span><span class="sxs-lookup"><span data-stu-id="bcda3-115">View and Modify Distributor and Publisher Properties</span></span>](view-and-modify-distributor-and-publisher-properties.md)   

 [<span data-ttu-id="bcda3-116">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="bcda3-116">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
