---
title: SQL Server 2005 レポートサーバー Web サービスグループが検出されました (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deployment [Reporting Services]
ms.assetid: 699d24eb-7756-4b41-9294-ef1a94b2f267
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 70be2b9c4e7abd55daaa752830a73cbe6e222659
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742794"
---
# <a name="sql-server-2005-report-server-web-service-group-detected-upgrade-advisor"></a><span data-ttu-id="193e9-102">SQL Server 2005 レポート サーバー Web サービス グループが検出された (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="193e9-102">SQL Server 2005 Report Server Web Service group detected (Upgrade Advisor)</span></span>
  <span data-ttu-id="193e9-103">アップグレードアドバイザーによっ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] て、インスタンスが [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポートサーバー Web サービスグループに関連付けられていることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="193e9-103">Upgrade Advisor detected that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is associated with a [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span>  
  
||  
|-|  
|<span data-ttu-id="193e9-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]ネイティブモード。</span><span class="sxs-lookup"><span data-stu-id="193e9-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="193e9-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="193e9-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="193e9-106">説明</span><span class="sxs-lookup"><span data-stu-id="193e9-106">Description</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="193e9-107">はを [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 使用し [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ません。レポートサーバー Web サービスグループ。</span><span class="sxs-lookup"><span data-stu-id="193e9-107">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] does not use the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="193e9-108">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードするときに、このサービス グループは削除され、このグループまたはグループに属するユーザーのカスタムのアクセス制御リスト (ACL) はアップグレード中に保持されません。</span><span class="sxs-lookup"><span data-stu-id="193e9-108">When you upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], this service group is deleted and custom Access Control Lists (ACLs) for this group or users who belong to the group are not retained during the upgrade.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="193e9-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="193e9-109">Corrective Action</span></span>  
 <span data-ttu-id="193e9-110">アップグレードする前に、すべてのカスタムの ACL または [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] レポート サーバー Web サービス グループに属するユーザーをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="193e9-110">Before you upgrade, back up any custom ACLs or users who belong to the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Report Server Web service group.</span></span> <span data-ttu-id="193e9-111">これを行うには、sp2 以降の**Icacls.exe**コマンドラインツール、 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] または sp2 より前の Windows オペレーティングシステムの Cacls.exe コマンドラインツールを使用でき [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="193e9-111">To do this, you can use the **Icacls.exe** command-line tool in [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2 and later or the Cacls.exe command-line tool in Windows operating systems prior to [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] SP2.</span></span> <span data-ttu-id="193e9-112">これらのツールの構文の詳細については、Windows の製品マニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="193e9-112">For more information about the syntax for these tools, see the Windows product documentation.</span></span> <span data-ttu-id="193e9-113">セットアップが正常に完了した後、カスタムの ACL またはユーザーを、レポート サーバー インスタンスの [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] レポート サーバー Windows グループに適用します。</span><span class="sxs-lookup"><span data-stu-id="193e9-113">After setup successfully completes, apply the custom ACLs or users to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group for your report server instance.</span></span> <span data-ttu-id="193e9-114">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]レポートサーバー Windows グループは、SQLServerReportServerUser $ の形式に \<*computer_name*> $ \<*instance_name*> なります。</span><span class="sxs-lookup"><span data-stu-id="193e9-114">The [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Report Server Windows group takes the form of SQLServerReportServerUser$\<*computer_name*>$\<*instance_name*>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="193e9-115">参照</span><span class="sxs-lookup"><span data-stu-id="193e9-115">See Also</span></span>  
 [<span data-ttu-id="193e9-116">アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="193e9-116">Reporting Services Upgrade Issues &#40;Upgrade Advisor&#41;</span></span>](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
