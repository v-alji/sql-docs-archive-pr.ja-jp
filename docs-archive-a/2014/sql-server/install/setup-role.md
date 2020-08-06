---
title: セットアップロール |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c7e9db15-89f2-4d4d-8860-1e64c5821c4d
author: heidisteen
ms.author: heidist
ms.openlocfilehash: add000eed671303c78ab0500303f826bafe4ab77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640414"
---
# <a name="setup-role"></a><span data-ttu-id="0cafb-102">セットアップ ロール</span><span class="sxs-lookup"><span data-stu-id="0cafb-102">Setup Role</span></span>
  <span data-ttu-id="0cafb-103">[機能の選択] ページを使用して個々の機能を選択するか、セットアップ ロールを使用してインストールするかを指定するには、このページを使用します。</span><span class="sxs-lookup"><span data-stu-id="0cafb-103">Use this page to specify whether to use the Feature Selection page to select individual features, or to install using a setup role.</span></span>  
  
 <span data-ttu-id="0cafb-104">`setup role` とは、事前定義された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成の実装に必要なすべての機能および共有コンポーネントを選択するために用意されている設定です。</span><span class="sxs-lookup"><span data-stu-id="0cafb-104">A `setup role` is a fixed selection of all the features and shared components that are required to implement a predefined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuration.</span></span>  
  
## <a name="options"></a><span data-ttu-id="0cafb-105">Options</span><span class="sxs-lookup"><span data-stu-id="0cafb-105">Options</span></span>  
 <span data-ttu-id="0cafb-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]機能のインストール**</span><span class="sxs-lookup"><span data-stu-id="0cafb-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Feature Installation**</span></span>  
 <span data-ttu-id="0cafb-107">個々の機能と共有コンポーネントを選択するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0cafb-107">Choose this option to select individual features and shared components.</span></span> <span data-ttu-id="0cafb-108">インスタンス機能には、データベース エンジン サービス、Analysis Services (ネイティブ モード)、Reporting Services などがあります。</span><span class="sxs-lookup"><span data-stu-id="0cafb-108">Instance features include Database Engine Services, Analysis Services (native mode), and Reporting Services.</span></span>  
  
 <span data-ttu-id="0cafb-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]PowerPivot for SharePoint**</span><span class="sxs-lookup"><span data-stu-id="0cafb-109">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for SharePoint**</span></span>  
 <span data-ttu-id="0cafb-110">SharePoint 2010 ファームに Analysis Services サーバー コンポーネントをインストールするには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0cafb-110">Choose this option to install Analysis Services server components in a SharePoint 2010 farm.</span></span> <span data-ttu-id="0cafb-111">このオプションを使用すると、PowerPivot System サービスおよび Analysis Services サーバーをファームに配置して、埋め込まれた [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを含むパブリッシュ済みの Excel ブックを対象としたクエリおよびデータ処理を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="0cafb-111">This option deploys the PowerPivot System Service and the Analysis Services server in a farm, enabling query and data processing for published Excel workbooks that contain embedded [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] data.</span></span>  
  
 <span data-ttu-id="0cafb-112">必要に応じて、SharePoint ファームでデータベースをホストするために必要なリレーショナル データベース エンジンのインスタンスをインストールに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="0cafb-112">Optionally, you can add a relational database engine instance to your installation if you require it to host databases in a SharePoint farm.</span></span> <span data-ttu-id="0cafb-113">既にファームが構成されている場合は、このオプションをスキップできます。</span><span class="sxs-lookup"><span data-stu-id="0cafb-113">If the farm is already configured, you can skip this option.</span></span>  
  
 <span data-ttu-id="0cafb-114">セットアップが完了したら、PowerPivot 構成ツール、PowerShell コマンドレット、SharePoint 2010 サーバーの全体管理のいずれかの方法でソフトウェアを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cafb-114">After Setup is finished, you must configure the software using one of the following approaches: PowerPivot Configuration tool, PowerShell cmdlets, or SharePoint 2010 Central Administration.</span></span> <span data-ttu-id="0cafb-115">以前のリリースとは異なり、セットアップでは PowerPivot インストールの構成タスクが実行されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0cafb-115">In contrast with previous releases, Setup no longer performs any configuration tasks for a PowerPivot installation.</span></span>  
  
 <span data-ttu-id="0cafb-116">ロール ベースのインストールには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel クライアント アプリケーションは含まれません。</span><span class="sxs-lookup"><span data-stu-id="0cafb-116">A role-based installation does not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerPivot for Excel client application.</span></span> <span data-ttu-id="0cafb-117">クライアント アプリケーションは個別にインストールします。</span><span class="sxs-lookup"><span data-stu-id="0cafb-117">The client application is installed separately.</span></span>  
  
 <span data-ttu-id="0cafb-118">**[すべての機能に既定値を使用]**</span><span class="sxs-lookup"><span data-stu-id="0cafb-118">**All Features With Defaults**</span></span>  
 <span data-ttu-id="0cafb-119">このリリースで使用できるすべての機能をインストールするには、このセットアップ ロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="0cafb-119">Choose this setup role to install all features that are available for this release.</span></span> <span data-ttu-id="0cafb-120">PowerPivot for SharePoint はこのロールから除外される点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="0cafb-120">Note that PowerPivot for SharePoint is excluded from this role.</span></span> <span data-ttu-id="0cafb-121">PowerPivot for SharePoint をインストールするには、PowerPivot for SharePoint セットアップ ロールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cafb-121">You must use the PowerPivot for SharePoint setup role to install that feature.</span></span>  
  
 <span data-ttu-id="0cafb-122">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は **NT AUTHORITY\NETWORK SERVICE** アカウントを使用して開始するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="0cafb-122">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is configured to start using the **NT AUTHORITY\NETWORK SERVICE** account.</span></span> <span data-ttu-id="0cafb-123">現在のユーザーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** ロールのメンバーとなります。</span><span class="sxs-lookup"><span data-stu-id="0cafb-123">The current user will be provisioned as a member of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**sysadmin** role.</span></span> <span data-ttu-id="0cafb-124">このオプションで設定した値は、他のコマンド ライン パラメーターを指定してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="0cafb-124">Values set by this option can be overridden by specifying additional command line parameters.</span></span>  
  
 <span data-ttu-id="0cafb-125">オペレーティング システムがドメイン コントローラーでない場合、既定ではデータベース エンジンおよび Reporting Services は NTAUTHORITY\NETWORK SERVICE アカウントを、Integration Services は NTAUTHORITY\NETWORK SERVICE アカウントを、SQL フルテキスト フィルター デーモン ランチャーは NTAUTHORITY\LOCAL SERVICE アカウントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0cafb-125">When the operating system is not a domain controller, by default the Database Engine and Reporting Services will use the NTAUTHORITY\NETWORK SERVICE account, Integration Services will use the NTAUTHORITY\NETWORK SERVICE account, and the SQL Full text Filter Daemon Launcher will use the NTAUTHORITY\LOCAL SERVICE account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cafb-126">参照</span><span class="sxs-lookup"><span data-stu-id="0cafb-126">See Also</span></span>  
 <span data-ttu-id="0cafb-127">[PowerPivot for SharePoint のインストール](https://go.microsoft.com/fwlink/?LinkId=206906) </span><span class="sxs-lookup"><span data-stu-id="0cafb-127">[Installing PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=206906) </span></span>  
 <span data-ttu-id="0cafb-128">[ハードウェアとソフトウェアの要件 (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span><span class="sxs-lookup"><span data-stu-id="0cafb-128">[Hardware and Software Requirements (PowerPivot for SharePoint](https://go.microsoft.com/fwlink/?LinkId=216823) </span></span>  
 [<span data-ttu-id="0cafb-129">特徴選択</span><span class="sxs-lookup"><span data-stu-id="0cafb-129">Feature Selection</span></span>](../../../2014/sql-server/install/feature-selection.md)  
  
  
