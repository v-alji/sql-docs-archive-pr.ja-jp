---
title: Integration Services Service | にアクセス許可を付与するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 0c2caa68-7834-4ea0-bd77-4f3a7c86d634
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0e7ab0c2f482e5a0b1bfeaa06f38ec5a886420a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632591"
---
# <a name="grant-permissions-to-integration-services-service"></a><span data-ttu-id="573a8-102">Integration Services サービスへの権限を付与する</span><span class="sxs-lookup"><span data-stu-id="573a8-102">Grant Permissions to Integration Services Service</span></span>
  <span data-ttu-id="573a8-103">以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をインストールすると、既定で Users グループの全ユーザーが [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスにアクセスできました。</span><span class="sxs-lookup"><span data-stu-id="573a8-103">In previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], by default when you installed [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] all users in the Users group had access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="573a8-104">現在のリリースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]をインストールした場合、ユーザーは [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="573a8-104">When you install the current release of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], users do not have access to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service.</span></span> <span data-ttu-id="573a8-105">このサービスは既定で保護されます。</span><span class="sxs-lookup"><span data-stu-id="573a8-105">The service is secure by default.</span></span> <span data-ttu-id="573a8-106">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインストール後に、管理者はサービスに対するアクセスを許可する必要があります。</span><span class="sxs-lookup"><span data-stu-id="573a8-106">After [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] is installed, the administrator must grant access to the service.</span></span>  
  
### <a name="to-grant-access-to-the-integration-services-service"></a><span data-ttu-id="573a8-107">Integration Services サービスへのアクセスを許可するには</span><span class="sxs-lookup"><span data-stu-id="573a8-107">To grant access to the Integration Services service</span></span>  
  
1.  <span data-ttu-id="573a8-108">Dcomcnfg.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="573a8-108">Run Dcomcnfg.exe.</span></span> <span data-ttu-id="573a8-109">Dcomcnfg.exe には、レジストリ内の特定の設定を変更するためのユーザー インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="573a8-109">Dcomcnfg.exe provides a user interface for modifying certain settings in the registry.</span></span>  
  
2.  <span data-ttu-id="573a8-110">**[コンポーネント サービス]** ダイアログで、[コンポーネント サービス] > [コンピューター] > [マイ コンピューター] > [DCOM の構成] ノードの順に展開します。</span><span class="sxs-lookup"><span data-stu-id="573a8-110">In the **Component Services** dialog, expand the Component Services > Computers > My Computer > DCOM Config node.</span></span>  
  
3.  <span data-ttu-id="573a8-111">**Microsoft SQL Server Integration Services 12.0**を右クリックし、[**プロパティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="573a8-111">Right-click **Microsoft SQL Server Integration Services 12.0**, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="573a8-112">**[セキュリティ]** タブで、 **[起動とアクティブ化のアクセス許可]** 領域の **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="573a8-112">On the **Security** tab, click **Edit** in the **Launch and Activation Permissions** area.</span></span>  
  
5.  <span data-ttu-id="573a8-113">ユーザーを追加し、適切なアクセス許可を割り当てて、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="573a8-113">Add users and assign appropriate permissions, and then click Ok.</span></span>  
  
6.  <span data-ttu-id="573a8-114">アクセス許可で手順 4. と 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="573a8-114">Repeat steps 4 - 5 for Access Permissions.</span></span>  
  
7.  <span data-ttu-id="573a8-115">SQL Server Management Studio を再起動します。</span><span class="sxs-lookup"><span data-stu-id="573a8-115">Restart SQL Server Management Studio.</span></span>  
  
8.  <span data-ttu-id="573a8-116">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="573a8-116">Restart the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Service.</span></span>  
  
  
