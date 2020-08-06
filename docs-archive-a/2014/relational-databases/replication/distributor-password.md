---
title: ディストリビューター パスワード | Microsoft Docs
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configuredistributionwizard.distributorpassword.f1
ms.assetid: 52787c5e-c9ef-440e-a000-0787111b7dbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 63e635903793bfa63d12b8a4cd2985178f9c4837
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632378"
---
# <a name="distributor-password"></a><span data-ttu-id="80971-102">[ディストリビューター パスワード]</span><span class="sxs-lookup"><span data-stu-id="80971-102">Distributor Password</span></span>
  <span data-ttu-id="80971-103">このサーバーをリモート ディストリビューターとして使用する 1 つ以上のパブリッシャーを、このウィザードの **[パブリッシャー]** ページで有効にしている場合は、レプリケーションが **distributor_admin** ログインを使用してパブリッシャーとリモート ディストリビューターとの間で確立する接続のパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80971-103">If, on the **Publishers** page of this wizard, you enabled one or more Publishers to use this server as a remote Distributor, you must specify a password for the connection replication makes between the Publisher and the remote Distributor using the **distributor_admin** login.</span></span> <span data-ttu-id="80971-104">このリモート ディストリビューターを使用するそれぞれのパブリッシャーに対して、パブリケーションの新規作成ウィザードまたはディストリビューションの構成ウィザードの **[管理パスワード]** ページに、同じパスワードを入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80971-104">The same password must be entered for each Publisher that uses this remote Distributor on the **Administrative Password** page of the New Publication Wizard or the Configure Distribution Wizard.</span></span> <span data-ttu-id="80971-105">ディストリビューターのセキュリティの詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80971-105">For more information on security for Distributors, see [Secure the Distributor](security/secure-the-distributor.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="80971-106">オプション</span><span class="sxs-lookup"><span data-stu-id="80971-106">Options</span></span>  
 <span data-ttu-id="80971-107">**パスワード**</span><span class="sxs-lookup"><span data-stu-id="80971-107">**Password**</span></span>  
 <span data-ttu-id="80971-108">パブリッシャーとリモート ディストリビューターとの間の接続に使用する複雑なパスワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="80971-108">Enter a strong password for the connection between the Publisher and the remote Distributor.</span></span>  
  
 <span data-ttu-id="80971-109">**[パスワードの確認入力]**</span><span class="sxs-lookup"><span data-stu-id="80971-109">**Confirm Password**</span></span>  
 <span data-ttu-id="80971-110">正しく入力されたことを確認するために、パスワードを再入力します。</span><span class="sxs-lookup"><span data-stu-id="80971-110">Re-enter the password to confirm it was entered correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80971-111">参照</span><span class="sxs-lookup"><span data-stu-id="80971-111">See Also</span></span>  
 <span data-ttu-id="80971-112">[[ディストリビューションの構成]](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="80971-112">[Configure Distribution](configure-distribution.md) </span></span>  
 [<span data-ttu-id="80971-113">パブリッシングおよびディストリビューションの構成</span><span class="sxs-lookup"><span data-stu-id="80971-113">Configure Publishing and Distribution</span></span>](configure-publishing-and-distribution.md)  
  
  
