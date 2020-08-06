---
title: 'レッスン 2: スケジュールに基づくベストプラクティスポリシーの評価 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 37ffad63-d6db-4609-8deb-786200659554
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a454e38ec2f07bf9867183a3894ac4ea001a942e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634181"
---
# <a name="lesson-2-evaluate-best-practices-policies-on-a-scheduled-basis"></a><span data-ttu-id="7a2db-102">レッスン 2: スケジュールに基づくベスト プラクティス ポリシーの評価</span><span class="sxs-lookup"><span data-stu-id="7a2db-102">Lesson 2: Evaluate Best Practices Policies on a Scheduled Basis</span></span>
  <span data-ttu-id="7a2db-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つ以上のインスタンスについて、スケジュールに基づくベスト プラクティス ポリシーの評価を構成できます。</span><span class="sxs-lookup"><span data-stu-id="7a2db-103">You can configure scheduled evaluations of best practices policies on one or more instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7a2db-104">ベスト プラクティス ポリシーをスケジュールに基づいて実行するよう構成するには、ポリシーを対象インスタンスにインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2db-104">To configure best practices policies to run on a scheduled basis, you must import the policies into the target instance.</span></span>  
  
 <span data-ttu-id="7a2db-105">スケジュールされたポリシーを複数のサーバーに配置するには、ポリシーを 1 つのインスタンスにインポートして、各ポリシーのスケジュールを構成し、スケジュールされたポリシーをフォルダーにエクスポートし、登録済みサーバーを通じてスケジュールされたポリシーを対象インスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="7a2db-105">To deploy scheduled policies to multiple servers, you can import the policies to one instance, configure the schedules for each policy, export the scheduled policies to a folder, and then deploy the scheduled policies to target instances through Registered Servers.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a2db-106">対象インスタンスは、[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] 以降のバージョンを実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a2db-106">The target instances must be running [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] or a later version.</span></span> <span data-ttu-id="7a2db-107">オートメーションではポリシーがインスタンス上にローカルに格納されている必要がありますが、これは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] より前のバージョンの [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7a2db-107">Automation requires the policies to be stored locally on the instance, which is not supported by versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are earlier than [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
 <span data-ttu-id="7a2db-108">このレッスンでは、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="7a2db-108">In this lesson, you will do the following:</span></span>  
  
-   <span data-ttu-id="7a2db-109">ベスト プラクティス ポリシーを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスにインポートします。</span><span class="sxs-lookup"><span data-stu-id="7a2db-109">Import the best practices policies into an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="7a2db-110">ポリシーをスケジュールに基づいて実行するよう構成します。</span><span class="sxs-lookup"><span data-stu-id="7a2db-110">Configure the policies to run on a schedule.</span></span>  
  
-   <span data-ttu-id="7a2db-111">スケジュールされたベスト プラクティス ポリシーを登録済みサーバーを通じて複数のインスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="7a2db-111">Deploy the scheduled best practices policies to multiple instances through Registered Servers.</span></span>  
  
 <span data-ttu-id="7a2db-112">このレッスンの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7a2db-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="7a2db-113">単一インスタンスへのポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="7a2db-113">Import the Policies to a Single Instance</span></span>](../../2014/tutorials/import-the-policies-to-a-single-instance.md)  
  
-   [<span data-ttu-id="7a2db-114">ポリシーのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="7a2db-114">Schedule the Policies</span></span>](../../2014/tutorials/schedule-the-policies.md)  
  
-   [<span data-ttu-id="7a2db-115">スケジュールされたポリシーの複数インスタンスへの配置</span><span class="sxs-lookup"><span data-stu-id="7a2db-115">Deploy Scheduled Policies to Multiple Instances</span></span>](../../2014/tutorials/deploy-scheduled-policies-to-multiple-instances.md)  
  
## <a name="see-also"></a><span data-ttu-id="7a2db-116">参照</span><span class="sxs-lookup"><span data-stu-id="7a2db-116">See Also</span></span>  
 [<span data-ttu-id="7a2db-117">中央管理サーバーを使用して複数のサーバーを管理する</span><span class="sxs-lookup"><span data-stu-id="7a2db-117">Administer Multiple Servers Using Central Management Servers</span></span>](../relational-databases/administer-multiple-servers-using-central-management-servers.md)  
  
  
