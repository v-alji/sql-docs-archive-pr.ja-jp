---
title: WMI Provider for Configuration Management での WQL およびスクリプト言語の使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- scripts [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Configuration Management, WQL
- WMI Provider for Configuration Management, scripts
ms.assetid: c1e64905-3c2b-4974-88f4-abf17cf7e289
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d8c903cd0e993728865bce3371c349a2d0ba7485
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640803"
---
# <a name="using-wql-and-scripting-languages-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="36efd-102">WQL およびスクリプティング言語での WMI Provider for Configuration Management の使用</span><span class="sxs-lookup"><span data-stu-id="36efd-102">Using WQL and Scripting Languages with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="36efd-103">管理アプリケーションが、WMI (Windows Management Instrumentation) Provider for Configuration Management オブジェクトを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定にアクセスするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="36efd-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings using the Windows Management Instrumentation (WMI) Provider for Configuration Management objects in two ways:</span></span>  
  
-   <span data-ttu-id="36efd-104">WQL エディターまたはクエリ ツール (WBEMTest.exe など) を使用して、WQL (WMI Query Language) でオブジェクト セットを照会する方法</span><span class="sxs-lookup"><span data-stu-id="36efd-104">Using a WQL editor or query tool, such as WBEMTest.exe to query the object set with the Windows Management Instrumentation Language (WQL).</span></span>  
  
-   <span data-ttu-id="36efd-105">VBScript などのスクリプティング言語を使用する方法</span><span class="sxs-lookup"><span data-stu-id="36efd-105">Using a scripting language, such as VBScript.</span></span>  
  
 <span data-ttu-id="36efd-106">または、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよびネットワーク設定は、SMO で WMI マネージド オブジェクトを使用してプログラムで管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="36efd-106">Alternatively, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings can be managed programmatically using the WMI managed objects in SMO.</span></span> <span data-ttu-id="36efd-107">WMI マネージオブジェクトのプログラミングの詳細については、「 [Wmi プロバイダーを使用したサービスとネットワーク設定の管理](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36efd-107">For more information about programming WMI managed objects, see [Managing Services and Network Settings by Using WMI Provider](../server-management-objects-smo/tasks/managing-services-and-network-settings-by-using-wmi-provider.md).</span></span>  
  
 <span data-ttu-id="36efd-108">WMI provider for Configuration Management には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] 管理コンソールを使用してアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="36efd-108">The WMI provider for Configuration Management can be accessed by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager and [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console.</span></span> <span data-ttu-id="36efd-109">ユーザーインターフェイスから WMI プロバイダーにアクセスする方法の詳細については、「[サービスの管理方法に関するトピック &#40;SQL Server 構成マネージャー&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36efd-109">For more information about accessing the WMI provider from a user interface, see [Managing Services How-to Topics &#40;SQL Server Configuration Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36efd-110">参照</span><span class="sxs-lookup"><span data-stu-id="36efd-110">See Also</span></span>  
 <span data-ttu-id="36efd-111">[WQL を使用した構成管理用 WMI プロバイダーへのアクセス](access-wmi-provider-for-configuration-management-using-wql.md) </span><span class="sxs-lookup"><span data-stu-id="36efd-111">[Access WMI Provider for Configuration Management using WQL](access-wmi-provider-for-configuration-management-using-wql.md) </span></span>  
 [<span data-ttu-id="36efd-112">VBScript を使用して SQL Server サービスの詳細プロパティを変更する</span><span class="sxs-lookup"><span data-stu-id="36efd-112">Modify SQL Server Service Advanced Properties using VBScript</span></span>](access-wmi-provider-for-configuration-management-using-vbscript.md)  
  
  
