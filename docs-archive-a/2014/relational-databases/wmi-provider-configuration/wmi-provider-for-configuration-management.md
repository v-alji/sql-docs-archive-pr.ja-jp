---
title: 構成管理のための WMI プロバイダーの概念 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- WMI Provider for Configuration Management
- SQL Server WMI Provider
- configuration management [WMI]
- WMI Provider for Configuration Management, about WMI Provider for Configuration Management
ms.assetid: 7e41db24-b915-4eb8-a1d6-e6948ee915b7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: be0682e7d6de5cb8c3d67a2f300bb89122213652
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634329"
---
# <a name="wmi-provider-for-configuration-management-concepts"></a><span data-ttu-id="55fdd-102">構成管理用の WMI プロバイダーの概念</span><span class="sxs-lookup"><span data-stu-id="55fdd-102">WMI Provider for Configuration Management Concepts</span></span>
  <span data-ttu-id="55fdd-103">WMI プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソール (MMC) および Configuration Manager の Configuration Manager スナップインと共に使用される、公開された層です [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="55fdd-103">The WMI provider is a published layer that is used with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager snap-in for [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console (MMC) and the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="55fdd-104">これにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーから要求されたレジストリ操作を処理する API 呼び出しは、統一されたインターフェイスで操作できます。また、選択された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスに対して高度な制御および操作を行えます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-104">It provides a unified way for interfacing with the API calls that manage the registry operations requested by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and provides enhanced control and manipulation over the selected [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services.</span></span>  
  
 <span data-ttu-id="55fdd-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによって自動的にコンパイルされる DLL ファイルおよび MOF ファイルです。</span><span class="sxs-lookup"><span data-stu-id="55fdd-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider is a DLL and a MOF file, which are compiled automatically by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 <span data-ttu-id="55fdd-106">WMI プロバイダーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次のメソッドを使用して、サービスを制御するために使用されるオブジェクトクラスのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55fdd-106">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider contains a set of object classes used to control the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services using the following methods:</span></span>  
  
-   <span data-ttu-id="55fdd-107">WQL (Windows Query Language) を埋め込むことができる VBScript、[!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)]、Perl などのスクリプト言語。</span><span class="sxs-lookup"><span data-stu-id="55fdd-107">A script language such as VBScript, [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)], or Perl, in which Windows Query Language (WQL) can be embedded.</span></span>  
  
-   <span data-ttu-id="55fdd-108">SMO マネージド コード プログラム内の <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="55fdd-108">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object in an SMO managed code program.</span></span>  
  
-   <span data-ttu-id="55fdd-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダー スナップインを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーまたは MMC。</span><span class="sxs-lookup"><span data-stu-id="55fdd-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager or MMC with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI provider snap-in.</span></span>  
  
## <a name="using-a-script-language"></a><span data-ttu-id="55fdd-110">スクリプト言語の使用</span><span class="sxs-lookup"><span data-stu-id="55fdd-110">Using a Script Language</span></span>  
 <span data-ttu-id="55fdd-111">スクリプト言語の使用には、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="55fdd-111">The advantages of using a script language include the following:</span></span>  
  
-   <span data-ttu-id="55fdd-112">開発環境が不要。</span><span class="sxs-lookup"><span data-stu-id="55fdd-112">A development environment is not required.</span></span>  
  
-   <span data-ttu-id="55fdd-113">スクリプト言語をサポートするファイルが幅広く利用可能。</span><span class="sxs-lookup"><span data-stu-id="55fdd-113">The files that support the script language are widely available.</span></span>  
  
 <span data-ttu-id="55fdd-114">スクリプトは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーに加えて、その他の WMI プロバイダーでも機能することができます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-114">The script can also work with other WMI Providers in addition to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI Provider.</span></span> <span data-ttu-id="55fdd-115">ドメイン管理者は、スクリプトを使用して、ネットワーク上の複数のコンピューターのサービスの設定、ネットワーク設定、および別名設定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-115">A domain administrator can use a script to set up the services, network settings, and alias settings on multiple computers on a network.</span></span>  
  
 <span data-ttu-id="55fdd-116">このセクションでは、スクリプトから構成管理用の WMI プロバイダーにアクセスする方法についてより詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="55fdd-116">This section deals with accessing the WMI Provider for Configuration Management from scripts in further detail.</span></span>  
  
## <a name="using-the-smo-managedcomputer-object"></a><span data-ttu-id="55fdd-117">SMO ManagedComputer オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="55fdd-117">Using the SMO ManagedComputer Object</span></span>  
 <span data-ttu-id="55fdd-118"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトは、構成管理用 WMI プロバイダーへのアクセスを提供する SMO マネージド オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="55fdd-118">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object is a managed SMO object that provides access to the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="55fdd-119">SMO プログラムを使用すると、<xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、ネットワーク設定、別名設定の表示と修正を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-119">By using an SMO program, the <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object can be used to view and modify [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and alias settings.</span></span> <span data-ttu-id="55fdd-120">詳細については、「 [WMI プロバイダーを使用したサービスとネットワーク設定の管理](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55fdd-120">For more information, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
## <a name="using-the-microsoft-management-console-or-sql-server-configuration-manager"></a><span data-ttu-id="55fdd-121">Microsoft 管理コンソールまたは SQL Server 構成マネージャーの使用</span><span class="sxs-lookup"><span data-stu-id="55fdd-121">Using the Microsoft Management Console or SQL Server Configuration Manager</span></span>  
 <span data-ttu-id="55fdd-122">Microsoft 管理コンソール (MMC) は、スクリプティング言語またはマネージド コード プログラムではなく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを管理するインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="55fdd-122">Microsoft Management Console (MMC) provides an interface to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, as opposed to a scripting language or managed code program.</span></span> <span data-ttu-id="55fdd-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理 MMC スナップインを使用して、サービスの停止や開始、およびサービス アカウントの変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-123">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management MMC snap-in can be used to stop and start services, and to change service accounts.</span></span>  
  
 <span data-ttu-id="55fdd-124">また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス、クライアント プロトコルとサーバー プロトコル、およびサーバー別名を管理することができます。</span><span class="sxs-lookup"><span data-stu-id="55fdd-124">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager can also be used to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, client and server protocols, and server aliases</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55fdd-125">参照</span><span class="sxs-lookup"><span data-stu-id="55fdd-125">See Also</span></span>  
 <span data-ttu-id="55fdd-126">[WMI Provider for Configuration Management について](understanding-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="55fdd-126">[Understanding the WMI Provider for Configuration Management](understanding-the-wmi-provider-for-configuration-management.md) </span></span>  
 <span data-ttu-id="55fdd-127">[WMI Provider for Configuration Management の使用](working-with-the-wmi-provider-for-configuration-management.md) </span><span class="sxs-lookup"><span data-stu-id="55fdd-127">[Working with the WMI Provider for Configuration Management](working-with-the-wmi-provider-for-configuration-management.md) </span></span>  
 [<span data-ttu-id="55fdd-128">WQL およびスクリプティング言語での WMI Provider for Configuration Management の使用</span><span class="sxs-lookup"><span data-stu-id="55fdd-128">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>](using-wql-and-scripting-languages-with-the-wmi-provider.md)  
  
  
