---
title: '[サーバーへの接続] (Oracle)、[ログイン] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.login.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 86ed91a1-a07c-46f2-a913-67317ef2255e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 23f5b515fcb1e80416d860e2ff3a2e6be5431819
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631830"
---
# <a name="connect-to-server-oracle-login"></a><span data-ttu-id="cec5d-102">[サーバーへの接続] (Oracle)、[ログイン]</span><span class="sxs-lookup"><span data-stu-id="cec5d-102">Connect to Server (Oracle), Login</span></span>
  <span data-ttu-id="cec5d-103">**[サーバーへの接続]** ダイアログ ボックスの **[ログイン]** タブを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターから Oracle パブリッシャーへの接続を確立するためのアカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cec5d-103">Use the **Login** tab of the **Connect to Server** dialog box to specify the account under which connections are made from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher.</span></span> <span data-ttu-id="cec5d-104">パブリッシャーの構成時にレプリケーション管理ユーザー スキーマ用に指定したものと同じアカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec5d-104">You must use the same account as the one specified for the replication administrative user schema during configuration of the Publisher.</span></span> <span data-ttu-id="cec5d-105">詳細については、「[Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cec5d-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="cec5d-106">オプション</span><span class="sxs-lookup"><span data-stu-id="cec5d-106">Options</span></span>  
 <span data-ttu-id="cec5d-107">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="cec5d-107">**Server instance**</span></span>  
 <span data-ttu-id="cec5d-108">ディストリビューターにインストールされた Oracle クライアント ソフトウェアの構成時に指定される、Oracle パブリッシャーの TNS (Transparent Network Substrate) 名です。</span><span class="sxs-lookup"><span data-stu-id="cec5d-108">The Transparent Network Substrate (TNS) name of the Oracle Publisher, which is specified during configuration of the Oracle client software installed on the Distributor.</span></span>  
  
 <span data-ttu-id="cec5d-109">**認証**</span><span class="sxs-lookup"><span data-stu-id="cec5d-109">**Authentication**</span></span>  
 <span data-ttu-id="cec5d-110">**[Oracle 標準認証]** (推奨) または **[Windows 認証]** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="cec5d-110">Select **Oracle Standard Authentication** (recommended) or **Windows Authentication**.</span></span> <span data-ttu-id="cec5d-111">**[Windows 認証]** を選択した場合 :</span><span class="sxs-lookup"><span data-stu-id="cec5d-111">If you select **Windows Authentication**:</span></span>  
  
-   <span data-ttu-id="cec5d-112">Oracle サーバーは、Windows 資格情報を使用して接続を許可するように構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec5d-112">The Oracle server must be configured to allow connections using Windows credentials.</span></span> <span data-ttu-id="cec5d-113">詳細については Oracle のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cec5d-113">For more information, see the Oracle documentation.</span></span>  
  
-   <span data-ttu-id="cec5d-114">現在、レプリケーション管理ユーザー スキーマ用に指定した [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントと同じものを使用してログインしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec5d-114">You must be currently logged in with the same [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account you specified for the replication administrative user schema.</span></span>  
  
 <span data-ttu-id="cec5d-115">**[ログイン]** と **[パスワード]**</span><span class="sxs-lookup"><span data-stu-id="cec5d-115">**Login** and **Password**</span></span>  
 <span data-ttu-id="cec5d-116">**[認証]** オプションの **[Oracle 標準認証]** を選択した場合は、使用するログインとパスワードを指定してください。レプリケーション管理ユーザー スキーマに指定したものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="cec5d-116">If you selected **Oracle Standard Authentication** for the **Authentication** option, specify the login and password to use, which must be the same as those specified for the replication administrative user schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec5d-117">参照</span><span class="sxs-lookup"><span data-stu-id="cec5d-117">See Also</span></span>  
 [<span data-ttu-id="cec5d-118">Oracle パブリッシングの用語</span><span class="sxs-lookup"><span data-stu-id="cec5d-118">Glossary of Terms for Oracle Publishing</span></span>](non-sql/glossary-of-terms-for-oracle-publishing.md)  
  
  
