---
title: 構成ファイルを使用した分散再生のインストール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3259232c-6963-4c9c-9d10-ae42aa262eef
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7757cce29c2e6b3ce4f1e91fc97cbf8be02ae521
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720882"
---
# <a name="install-distributed-replay-using-a-configuration-file"></a><span data-ttu-id="9dfb2-102">構成ファイルを使用した 分散再生のインストール</span><span class="sxs-lookup"><span data-stu-id="9dfb2-102">Install Distributed Replay Using a Configuration File</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="9dfb2-103">セットアップには、ユーザー入力およびシステムの既定値に基づいて構成ファイルを生成する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-103">Setup provides the ability to generate a configuration file based on user input and system defaults.</span></span> <span data-ttu-id="9dfb2-104">管理ツールをインストールするように指定すると、構成ファイルを使用して、3 つの 分散再生コンポーネント (管理ツール、分散再生コントローラー、および分散再生クライアント) を配置できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-104">If you specify that you want the Management tools installed, you can use the configuration file to deploy the three Distributed Replay components (administration tool, Distributed Replay controller, and the Distributed Replay client).</span></span> <span data-ttu-id="9dfb2-105">SQL Server セットアップでは、分散再生ユーティリティ コンポーネントのインストール、修復、およびアンインストールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-105">It supports Installing, repairing, and uninstalling of the Distributed Replay components.</span></span>  
  
 <span data-ttu-id="9dfb2-106">セットアップでは、コマンド ラインからのみ構成ファイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-106">Setup supports the use of the configuration file only through the command-line.</span></span> <span data-ttu-id="9dfb2-107">以下に、構成ファイルを使用する際のパラメーターの処理順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-107">The processing order of the parameters while using the configuration file is outlined below:</span></span>  
  
-   <span data-ttu-id="9dfb2-108">構成ファイルによって、パッケージの既定値が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-108">The configuration file overwrites the defaults in a package</span></span>  
  
-   <span data-ttu-id="9dfb2-109">コマンド ライン値によって、構成ファイル内の値が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-109">Command-line values overwrite the values in the configuration file</span></span>  
  
 <span data-ttu-id="9dfb2-110">構成ファイルの使用方法の詳細については、「[構成ファイルを使用した SQL Server 2014 のインストール](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-110">For more information about how to use a configuration file, see [Install SQL Server 2014 Using a Configuration File](../../database-engine/install-windows/install-sql-server-using-a-configuration-file.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9dfb2-111">分散再生をインストールした後、コントローラー コンピューターとクライアント コンピューターのファイアウォール ルールを作成し、ターゲット サーバー上で各クライアント コンピューターの権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-111">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="9dfb2-112">詳細については、「 [インストール後の手順の実行](../../tools/distributed-replay/complete-the-post-installation-steps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-112">For more information, see [Complete the Post-Installation Steps](../../tools/distributed-replay/complete-the-post-installation-steps.md).</span></span>  
  
### <a name="to-generate-a-configuration-file"></a><span data-ttu-id="9dfb2-113">構成ファイルを生成するには</span><span class="sxs-lookup"><span data-stu-id="9dfb2-113">To generate a configuration file</span></span>  
  
1.  <span data-ttu-id="9dfb2-114">セットアップ ウィザードに従って **[インストールの準備完了]** ページまで進みます。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-114">Follow the Setup wizard through to the **Ready to Install** page.</span></span> <span data-ttu-id="9dfb2-115">構成ファイルのパスは、 **[インストールの準備完了]** ページの [構成ファイルのパス] セクションで指定します。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-115">The path to the configuration file is specified in the **Ready to Install** page in the configuration file path section.</span></span>  
  
2.  <span data-ttu-id="9dfb2-116">INI ファイルを生成するには、インストールを実際に完了しなくてもセットアップを取り消します。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-116">Cancel the setup without actually completing the installation, to generate the INI file.</span></span>  
  
### <a name="to-install-distributed-replay-using-the-configuration-file"></a><span data-ttu-id="9dfb2-117">構成ファイルを使用して 分散再生をインストールするには</span><span class="sxs-lookup"><span data-stu-id="9dfb2-117">To Install Distributed Replay Using the Configuration File</span></span>  
  
-   <span data-ttu-id="9dfb2-118">コマンド プロンプトからインストールを実行し、ConfigurationFile パラメーターを使用して ConfigurationFile.ini を指定します。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-118">Run the installation through the command prompt and supply the ConfigurationFile.ini using the ConfigurationFile parameter.</span></span>  
  
 <span data-ttu-id="9dfb2-119">**サンプル構文**</span><span class="sxs-lookup"><span data-stu-id="9dfb2-119">**Sample Syntax**</span></span>  
  
 <span data-ttu-id="9dfb2-120">次の例では、コマンド プロンプトで構成ファイルを指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-120">Following is an example on how to specify the configuration file at the command prompt:</span></span>  
  
```  
Setup.exe /CTLRSVCPASSWORD="ctlrsvcpswd" /CLTSVCPASSWORD="cltsvcpswd" / ConfigurationFile=ConfigurationFile.INI\  
```  
  
> [!NOTE]  
>  <span data-ttu-id="9dfb2-121">構成ファイルでパスワードを構成することはできないため、コマンドラインで両方のパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dfb2-121">You must specify both passwords in the command line because you cannot configure them in the configuration file.</span></span>  
  
  
