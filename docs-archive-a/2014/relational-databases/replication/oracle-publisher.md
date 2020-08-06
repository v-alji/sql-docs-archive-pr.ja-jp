---
title: Oracle パブリッシャー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.selectoraclepublisher.f1
ms.assetid: 019b7c49-dcca-445d-8969-5982a8ccbc1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: db52b93b3d260ff58a151e7238bbbe065bc47bc0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631808"
---
# <a name="oracle-publisher"></a><span data-ttu-id="8451d-102">Oracle パブリッシャー</span><span class="sxs-lookup"><span data-stu-id="8451d-102">Oracle Publisher</span></span>
  <span data-ttu-id="8451d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、スナップショット レプリケーションおよびトランザクション レプリケーションを使用して、Oracle データベースからデータをパブリッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="8451d-103">Beginning with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] allows you to publish data from an Oracle database using snapshot and transactional replication.</span></span> <span data-ttu-id="8451d-104">詳細については、「[Oracle パブリッシングの概要](non-sql/oracle-publishing-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8451d-104">For more information, see [Oracle Publishing Overview](non-sql/oracle-publishing-overview.md).</span></span>  
  
 <span data-ttu-id="8451d-105">Oracle パブリッシャーでは、リモート [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターを使用する必要があります。そのため、このウィザードは、必要な Oracle ネットワーク ソフトウェアのインストールとテストが行われた後のサーバーで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8451d-105">The Oracle Publisher must use a remote [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor; this wizard must be run on that server after the necessary Oracle networking software has been installed and tested.</span></span> <span data-ttu-id="8451d-106">詳細については、「[Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8451d-106">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8451d-107">他の管理者が Oracle データベースをパブリッシャーとして構成している場合、 **[次へ]** をクリックすると Oracle データベースへの接続に使用されるレプリケーション ログインのパスワードを入力するよう求められます。</span><span class="sxs-lookup"><span data-stu-id="8451d-107">If another administrator configured the Oracle database as a Publisher, after clicking **Next** you will be prompted to enter the password for the replication login used to connect to the Oracle database.</span></span> <span data-ttu-id="8451d-108">入力すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、ログインと Oracle データベースへのリンク サーバー接続の間のマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8451d-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will then create a mapping between your login and the linked server connection to the Oracle database.</span></span> <span data-ttu-id="8451d-109">以降の Oracle データベースへの接続にパスワードの入力が求められることはありません。</span><span class="sxs-lookup"><span data-stu-id="8451d-109">You will not be required to enter a password for subsequent connections to the Oracle database.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8451d-110">オプション</span><span class="sxs-lookup"><span data-stu-id="8451d-110">Options</span></span>  
 <span data-ttu-id="8451d-111">**Oracle パブリッシャー**</span><span class="sxs-lookup"><span data-stu-id="8451d-111">**Oracle Publishers**</span></span>  
 <span data-ttu-id="8451d-112">一覧から Oracle パブリッシャーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8451d-112">Select an Oracle Publisher from the list.</span></span> <span data-ttu-id="8451d-113">この一覧には、ウィザードがディストリビューターとして実行されているサーバーを使用するように、以前に構成されたことのある Oracle パブリッシャーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8451d-113">This list contains Oracle Publishers that have previously been configured to use the server against which the wizard is running as their Distributor.</span></span> <span data-ttu-id="8451d-114">この一覧が空の場合や使用する Oracle パブリッシャーが一覧にない場合は、 **[Oracle パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8451d-114">If the list is empty, or the Oracle Publisher you want to use is not in the list, click **Add Oracle Publisher**.</span></span>  
  
 <span data-ttu-id="8451d-115">**[Oracle パブリッシャーの追加]**</span><span class="sxs-lookup"><span data-stu-id="8451d-115">**Add Oracle Publisher**</span></span>  
 <span data-ttu-id="8451d-116">**[ディストリビューターのプロパティ]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8451d-116">Click to launch the **Distributor Properties** dialog box.</span></span> <span data-ttu-id="8451d-117">このダイアログ ボックスで、 **[追加]** をクリックして、 **[Oracle パブリッシャーの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8451d-117">In this dialog box, click **Add**, and then click **Add Oracle Publisher**.</span></span> <span data-ttu-id="8451d-118">**[サーバーへの接続]** ダイアログ ボックスで、Oracle サーバー名およびレプリケーション管理ユーザー スキーマのログインとパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8451d-118">In the **Connect to Server** dialog box, specify the Oracle server name, and the login and password for the replication administrative user schema.</span></span> <span data-ttu-id="8451d-119">詳細については、「[[サーバーへの接続] &#40;Oracle&#41;、[ログイン]](connect-to-server-oracle-login.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8451d-119">For more information, see [Connect to Server &#40;Oracle&#41;, Login](connect-to-server-oracle-login.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8451d-120">このウィザードが実行されているサーバーがディストリビューターとしてまだ構成されていない場合、ディストリビューターを構成するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="8451d-120">If the server against which the wizard is running has not yet been configured as a Distributor, you are prompted to configure it now.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8451d-121">参照</span><span class="sxs-lookup"><span data-stu-id="8451d-121">See Also</span></span>  
 [<span data-ttu-id="8451d-122">Oracle データベースからのパブリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="8451d-122">Create a Publication from an Oracle Database</span></span>](publish/create-a-publication-from-an-oracle-database.md)   

  
  
