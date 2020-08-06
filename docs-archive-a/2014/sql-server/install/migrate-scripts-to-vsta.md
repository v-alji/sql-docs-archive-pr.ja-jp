---
title: スクリプトを VSTA | に移行するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: afbc19c35f99a5abc5a6ebd92024e42baa6a9237
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740701"
---
# <a name="migrate-scripts-to-vsta"></a><span data-ttu-id="cda82-102">VSTA へのスクリプトの移行</span><span class="sxs-lookup"><span data-stu-id="cda82-102">Migrate Scripts to VSTA</span></span>
  <span data-ttu-id="cda82-103">パッケージをにアップグレードすると [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、では、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] スクリプトタスクまたはスクリプトコンポーネント内のスクリプトが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) に移行されます。</span><span class="sxs-lookup"><span data-stu-id="cda82-103">When you upgrade [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] packages to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] migrates the scripts in any Script tasks or Script components to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA).</span></span> <span data-ttu-id="cda82-104">VSTA は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で使用されるスクリプト環境です。</span><span class="sxs-lookup"><span data-stu-id="cda82-104">VSTA is the scripting environment that [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] uses.</span></span> <span data-ttu-id="cda82-105">で [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] は、のスクリプト環境 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA) です。</span><span class="sxs-lookup"><span data-stu-id="cda82-105">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the scripting environment for [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] for Applications (VSA).</span></span>  
  
 <span data-ttu-id="cda82-106">スクリプト タスクまたはスクリプト コンポーネント内のスクリプトでインターフェイスを参照している場合、パッケージをアップグレードする前にそれらの参照の変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cda82-106">If the scripts in either the Script tasks or Script components reference interfaces, you might have to modify those references before you upgrade the package.</span></span> <span data-ttu-id="cda82-107">参照を変更しないと、使用するアップグレード方法によってはパッケージをアップグレードできないかスクリプトを検証できません。</span><span class="sxs-lookup"><span data-stu-id="cda82-107">Otherwise, the package will not be upgraded or the scripts will not be validated, depending on the upgrade method that you use.</span></span> <span data-ttu-id="cda82-108">これらの参照を変更するには、IDTS*xxx*90 インターフェイスへの参照を、対応する idts*xxx*100 インターフェイスへの参照に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cda82-108">To modify these references, replace references to IDTS*xxx*90 interfaces with references to the corresponding IDTS*xxx*100 interfaces.</span></span>  
  
 <span data-ttu-id="cda82-109">スクリプトの移行方法とパッケージのアップグレード方法の詳細については、「 [Integration Services パッケージのアップグレード](../../integration-services/install-windows/upgrade-integration-services-packages.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cda82-109">For more information about how to migrate scripts and upgrade packages, see [Upgrade Integration Services Packages](../../integration-services/install-windows/upgrade-integration-services-packages.md).</span></span>  
  
## <a name="understanding-migration-failures"></a><span data-ttu-id="cda82-110">移行エラーについて</span><span class="sxs-lookup"><span data-stu-id="cda82-110">Understanding Migration Failures</span></span>  
 <span data-ttu-id="cda82-111">スクリプトを移行する際、次の理由により移行が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="cda82-111">When you migrate the scripts, the migration can fail because of one of the following reasons:</span></span>  
  
-   <span data-ttu-id="cda82-112">VSA スクリプトのエントリ ポイント名が変更された。</span><span class="sxs-lookup"><span data-stu-id="cda82-112">The entry point for the VSA script was renamed.</span></span>  
  
     <span data-ttu-id="cda82-113">エントリ ポイントは、スクリプト タスク コードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出す、VSTA プロジェクトの `ScriptMain` クラスのメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="cda82-113">The entry point specifies the method in the `ScriptMain` class in the VSTA project that the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] runtime calls as the entry point into the Script task code.</span></span> <span data-ttu-id="cda82-114">クラスは、スクリプトテンプレートによって `ScriptMain` 生成される既定のクラスです。</span><span class="sxs-lookup"><span data-stu-id="cda82-114">The `ScriptMain` class is the default class that the script templates generate.</span></span>  
  
-   <span data-ttu-id="cda82-115">VSA スクリプトにエントリ ポイントがないか、複数のエントリ ポイントがある。</span><span class="sxs-lookup"><span data-stu-id="cda82-115">There is no entry point or there are multiple entry points in the VSA script.</span></span>  
  
-   <span data-ttu-id="cda82-116">アセンブリ参照を追加できなかった。</span><span class="sxs-lookup"><span data-stu-id="cda82-116">Assembly references could not be added.</span></span>  
  
-   <span data-ttu-id="cda82-117">`ScriptMain` クラスが、`ScriptObjectModelSSIS` クラス以外にもクラスを継承するように変更された。</span><span class="sxs-lookup"><span data-stu-id="cda82-117">The `ScriptMain` class was modified to inherit from other classes in addition to the `ScriptObjectModelSSIS` class.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="cda82-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]では、多重継承はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cda82-118">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] does not support multiple inheritance.</span></span>  
  
 <span data-ttu-id="cda82-119">を使用する VSA スクリプトを、 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] を使用する VSTA スクリプトに変換することはできません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cda82-119">You cannot convert a VSA script that uses [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] to a VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="cda82-120">ただし、を使用する新しい VSTA スクリプトを作成でき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="cda82-120">However, you can create a new VSTA script that uses [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)].</span></span> <span data-ttu-id="cda82-121">詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/control-flow/script-task.md)」および「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/data-flow/transformations/script-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cda82-121">For more information, see [Coding and Debugging the Script Task](../../integration-services/control-flow/script-task.md) and [Coding and Debugging the Script Component](../../integration-services/data-flow/transformations/script-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda82-122">参照</span><span class="sxs-lookup"><span data-stu-id="cda82-122">See Also</span></span>  
 [<span data-ttu-id="cda82-123">スクリプトによるパッケージの拡張</span><span class="sxs-lookup"><span data-stu-id="cda82-123">Extending Packages with Scripting</span></span>](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
