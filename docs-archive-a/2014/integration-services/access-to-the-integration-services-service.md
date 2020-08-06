---
title: Integration Services サービスへのアクセス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7dd6fbed4bedc285069306ab4c400f0f67f9f293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633281"
---
# <a name="access-to-the-integration-services-service"></a><span data-ttu-id="d4acc-102">Integration Services サービスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="d4acc-102">Access to the Integration Services Service</span></span>
  <span data-ttu-id="d4acc-103">パッケージの保護レベルによって、パッケージを編集および実行できるユーザーを制限できます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-103">Package protection levels can limit who is allowed to edit and execute a package.</span></span> <span data-ttu-id="d4acc-104">サーバーで現在実行中のパッケージの一覧を表示できるユーザー、および [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]で現在実行中のパッケージを停止できるユーザーを制限するには、追加の保護が必要です。</span><span class="sxs-lookup"><span data-stu-id="d4acc-104">Additional protection is needed to limit who can view the list of packages currently running on a server and who can stop currently executing packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] <span data-ttu-id="d4acc-105">では、実行中のパッケージを一覧表示する際に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-105">uses the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service to list running packages.</span></span> <span data-ttu-id="d4acc-106">Windows の Administrators グループのメンバーは、実行中のすべてのパッケージを表示および停止できます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-106">Members of the Windows Administrators group can view and stop all currently running packages.</span></span> <span data-ttu-id="d4acc-107">Administrators グループのメンバーではないユーザーは、本人が起動したパッケージのみを表示および停止できます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-107">Users who are not members of the Administrators group can view and stop only packages that they started.</span></span>  
  
 <span data-ttu-id="d4acc-108">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス (特に、リモート フォルダーの列挙を行う可能性のある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス) を実行するコンピューターへのアクセスを制限することは重要です。</span><span class="sxs-lookup"><span data-stu-id="d4acc-108">It is important to restrict access to computers that run an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service, especially an [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] service that can enumerate remote folders.</span></span> <span data-ttu-id="d4acc-109">認証を受けたユーザーであれば、パッケージの列挙を要求できます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-109">Any authenticated user can request the enumeration of packages.</span></span> <span data-ttu-id="d4acc-110">サービスが見つからない場合でも、サービスはフォルダーを列挙します。</span><span class="sxs-lookup"><span data-stu-id="d4acc-110">Even if the service doesn not find the service, the service enumerates folders.</span></span> <span data-ttu-id="d4acc-111">これらのフォルダー名が、悪意あるユーザーに悪用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d4acc-111">These folder names may be useful to a malicious user.</span></span> <span data-ttu-id="d4acc-112">管理者がリモート コンピューターのフォルダーを列挙できるようにサービスを設定した場合、ユーザーも通常は参照できないフォルダー名を参照することができます。</span><span class="sxs-lookup"><span data-stu-id="d4acc-112">If an administrator has configured the service to enumerate folders on a remote machine, users may also be able to see folder names that they would normally not be able to see.</span></span>  
  
  
