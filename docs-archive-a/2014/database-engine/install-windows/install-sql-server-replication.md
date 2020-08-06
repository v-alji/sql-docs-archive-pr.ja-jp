---
title: SQL Server レプリケーションのインストール | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- components [SQL Server replication]
- command line installations [SQL Server replication]
- installing replication
- replication [SQL Server], installing
- command prompt [SQL Server replication]
ms.assetid: c50ad078-060b-4a8d-ad45-9e31a8d85729
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ba941fda1d463e7bb4a26bd2fbb45d2a82ca27b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713441"
---
# <a name="install-sql-server-replication"></a><span data-ttu-id="88fb5-102">SQL Server レプリケーションのインストール</span><span class="sxs-lookup"><span data-stu-id="88fb5-102">Install SQL Server Replication</span></span>
  <span data-ttu-id="88fb5-103">レプリケーション コンポーネントのインストールは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール ウィザードまたはコマンド プロンプトを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="88fb5-103">Replication components can be installed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard or at a command prompt.</span></span> <span data-ttu-id="88fb5-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をインストールする場合、または既存のインスタンスを変更する場合はレプリケーションをインストールします。</span><span class="sxs-lookup"><span data-stu-id="88fb5-104">Install replication when you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or when you modify an existing instance.</span></span>  
  
 <span data-ttu-id="88fb5-105">レプリケーション コンポーネントのインストール後、レプリケーションを使用する前にサーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88fb5-105">After replication components are installed, you must configure the server before you can use replication.</span></span> <span data-ttu-id="88fb5-106">詳細については、 [オンライン ブックの「](../../relational-databases/replication/configure-distribution.md) ディストリビューションの構成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88fb5-106">For more information, see [Configure Distribution](../../relational-databases/replication/configure-distribution.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="88fb5-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の既存のインスタンスを変更するときにレプリケーション コンポーネントをインストールする場合は、インストール完了後に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを停止して再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88fb5-107">If you install replication components when you modify an existing instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], you must stop and restart [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent after the installation is completed.</span></span> <span data-ttu-id="88fb5-108">この操作により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがレプリケーション エージェント サブシステムを認識し、ジョブ ステップからレプリケーション エージェントを呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="88fb5-108">This action helps ensure that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent recognizes the replication agent subsystems and can call replication agents from job steps.</span></span>  
  
## <a name="installing-replication-by-using-setup"></a><span data-ttu-id="88fb5-109">セットアップ プログラムによるレプリケーションのインストール</span><span class="sxs-lookup"><span data-stu-id="88fb5-109">Installing Replication by Using Setup</span></span>  
 <span data-ttu-id="88fb5-110">**の新しいインスタンスをインストールするときにレプリケーションをインストールするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="88fb5-110">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="88fb5-111">レプリケーション管理オブジェクト (RMO) を含めてレプリケーション コンポーネントをインストールするには、インストール ウィザードの **[機能の選択]** ページで **[SQL Server レプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="88fb5-111">To install replication components, including Replication Management Objects (RMO), select **SQL Server Replication** on the **Feature Selection** page of the Installation Wizard.</span></span>  
  
## <a name="installing-replication-from-the-command-prompt"></a><span data-ttu-id="88fb5-112">コマンド プロンプトによるレプリケーションのインストール</span><span class="sxs-lookup"><span data-stu-id="88fb5-112">Installing Replication from the Command Prompt</span></span>  
 <span data-ttu-id="88fb5-113">**の新しいインスタンスをインストールするときにレプリケーションをインストールするには [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="88fb5-113">**To install replication when installing a new instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**</span></span>  
  
-   <span data-ttu-id="88fb5-114">「[コマンドプロンプトから SQL Server 2014 をインストールする」を](install-sql-server-from-the-command-prompt.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="88fb5-114">See [Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fb5-115">参照</span><span class="sxs-lookup"><span data-stu-id="88fb5-115">See Also</span></span>  
 <span data-ttu-id="88fb5-116">[SQL Server 2014 をインストールする](install-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="88fb5-116">[Install SQL Server 2014](install-sql-server.md) </span></span>  
 <span data-ttu-id="88fb5-117">[コマンドプロンプトから SQL Server 2014 をインストールする](install-sql-server-from-the-command-prompt.md) </span><span class="sxs-lookup"><span data-stu-id="88fb5-117">[Install SQL Server 2014 from the Command Prompt](install-sql-server-from-the-command-prompt.md) </span></span>  
 [<span data-ttu-id="88fb5-118">SQL Server 2014 の各エディションがサポートする機能</span><span class="sxs-lookup"><span data-stu-id="88fb5-118">Features Supported by the Editions of SQL Server 2014</span></span>](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)  
  
  
