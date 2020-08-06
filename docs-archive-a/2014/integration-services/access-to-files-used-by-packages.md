---
title: パッケージによって使用されるファイルへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- packages [Integration Services], security
- configuration files [Integration Services]
- checkpoint files
- Integration Services packages, security
- logs [Integration Services], security
- files [Integration Services], security
- SQL Server Integration Services packages, security
ms.assetid: 2e3ddea9-5289-4289-a70e-11c018f34977
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8db9511c91c9f229b7002f5b16cf077910a4ccf0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633286"
---
# <a name="access-to-files-used-by-packages"></a><span data-ttu-id="2cbd4-102">パッケージで使用されるファイルへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2cbd4-102">Access to Files Used by Packages</span></span>
  <span data-ttu-id="2cbd4-103">パッケージに格納されないファイルは、パッケージ保護レベルでは保護されません。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-103">The package protection level does not protect files that are stored outside the package.</span></span> <span data-ttu-id="2cbd4-104">このようなファイルには、次のファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-104">These files include the following:</span></span>  
  
-   <span data-ttu-id="2cbd4-105">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-105">Configuration files</span></span>  
  
-   <span data-ttu-id="2cbd4-106">チェックポイント ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-106">Checkpoint files</span></span>  
  
-   <span data-ttu-id="2cbd4-107">ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-107">Log files</span></span>  
  
 <span data-ttu-id="2cbd4-108">特に機密情報が含まれている場合、これらのファイルは個別に保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-108">These files must be protected separately, especially if they include sensitive information.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2cbd4-109">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-109">Configuration Files</span></span>  
 <span data-ttu-id="2cbd4-110">ログイン情報やパスワード情報などの機密情報が構成に含まれている場合は、その構成を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に保存することを検討するか、アクセス制御リスト (ACL) を使用して、ファイルを保存する場所またはフォルダーへのアクセスを制限し、特定のアカウントにのみアクセスを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-110">If you have sensitive information in a configuration, such as login and password information, you should consider saving the configuration to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], or use an access control list (ACL) to restrict access to the location or folder where you store the files and allow access only to certain accounts.</span></span> <span data-ttu-id="2cbd4-111">通常は、パッケージの実行を許可するアカウント、およびパッケージの管理とトラブルシューティング (構成の内容、チェックポイント、およびログ ファイルの確認) を行うアカウントにアクセス権を許可します。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-111">Typically, you would grant access to the accounts that you permit to run packages, and to the accounts that manage and troubleshoot packages, which may include reviewing the contents of configuration, checkpoint, and log files.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="2cbd4-112">では、サーバー レベルおよびデータベース レベルでの保護により、さらに堅牢なセキュリティが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-112">provides the more secure storage because it offers protection at the server and database levels.</span></span> <span data-ttu-id="2cbd4-113">構成を [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に保存するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-113">To save configurations to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you use the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] configuration type.</span></span> <span data-ttu-id="2cbd4-114">ファイル システムに保存するには、XML 構成の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-114">To save to the file system, you use the XML configuration type.</span></span>  
  
 <span data-ttu-id="2cbd4-115">詳細については、「 [パッケージ構成](../../2014/integration-services/package-configurations.md)」、「 [パッケージ構成を作成する](../../2014/integration-services/create-package-configurations.md)」、および「 [SQL Server インストールにおけるセキュリティの考慮事項](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-115">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md), [Create Package Configurations](../../2014/integration-services/create-package-configurations.md), and [Security Considerations for a SQL Server Installation](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
## <a name="checkpoint-files"></a><span data-ttu-id="2cbd4-116">チェックポイント ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-116">Checkpoint Files</span></span>  
 <span data-ttu-id="2cbd4-117">同様に、パッケージで使用するチェックポイント ファイルに機密情報が含まれている場合も、アクセス制御リスト (ACL) を使用して、ファイルが格納されている場所またはフォルダーを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-117">Similarly, if the checkpoint file that the package uses includes sensitive information, you should use an access control list (ACL) to secure the location or folder where you store the file.</span></span> <span data-ttu-id="2cbd4-118">チェックポイント ファイルは、パッケージの進行状況に関する現在の状態情報と変数の現在の値を格納します。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-118">Checkpoint files save current state information on the progress of the package as well as the current values of variables.</span></span> <span data-ttu-id="2cbd4-119">たとえば、電話番号を格納するカスタム変数がパッケージに含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-119">For example, the package may include a custom variable that contains a telephone number.</span></span> <span data-ttu-id="2cbd4-120">詳細については、「 [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-120">For more information, see [Restart Packages by Using Checkpoints](packages/restart-packages-by-using-checkpoints.md).</span></span>  
  
## <a name="log-files"></a><span data-ttu-id="2cbd4-121">ログ ファイル</span><span class="sxs-lookup"><span data-stu-id="2cbd4-121">Log Files</span></span>  
 <span data-ttu-id="2cbd4-122">ファイル システムに書き込まれるログ エントリも、アクセス制御リスト (ACL) を使用して保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-122">Log entries that are written to the file system should also be secured using an access control list (ACL).</span></span> <span data-ttu-id="2cbd4-123">ログ エントリは、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルに保存して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] セキュリティで保護することもできます。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-123">Log entries can also be stored in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tables and protected by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] security.</span></span> <span data-ttu-id="2cbd4-124">ログ エントリには機密情報が含まれることがあります。たとえば、パッケージに含まれる SQL 実行タスクによって、電話番号を参照する SQL ステートメントが構築される場合、SQL ステートメントのログ エントリにも電話番号が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-124">Log entries may include sensitive information, For example, if the package contains an Execute SQL task that constructs an SQL statement that refers to a telephone number, the log entry for the SQL statement includes the telephone number.</span></span> <span data-ttu-id="2cbd4-125">また、SQL ステートメントにより、データベース内のテーブル名や列名に関するプライベートな情報が明らかにされる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-125">The SQL statement may also reveal private information about table and column names in databases.</span></span> <span data-ttu-id="2cbd4-126">詳細については、「[Integration Services (SSIS) のログ記録](performance/integration-services-ssis-logging.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2cbd4-126">For more information, see [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md).</span></span>  
  
  
