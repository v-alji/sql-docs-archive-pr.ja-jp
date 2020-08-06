---
title: マルチサーバー環境に適した SQL Server エージェントサービスアカウントを選択してください |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: stevestein
ms.author: sstein
ms.openlocfilehash: 94ef890f5d2ef2b85d2f4d1023a93747e903a7f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645344"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a><span data-ttu-id="985f7-102">マルチサーバー環境に適した SQL Server エージェント サービス アカウントの選択</span><span class="sxs-lookup"><span data-stu-id="985f7-102">Choose the Right SQL Server Agent Service Account for Multiserver Environments</span></span>
  <span data-ttu-id="985f7-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスに対して選択する Windows アカウントによって、マルチサーバー環境の動作に次のような影響が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="985f7-103">The Windows account you choose for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can affect the behavior of a multiserver environment, as follows:</span></span>  
  
-   <span data-ttu-id="985f7-104">ローカルの Windows Administrators グループのメンバーではないアカウントで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを実行する場合、マスター サーバーへのターゲット サーバーの参加は、失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="985f7-104">If you run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service under an account that is not a member of the local Windows Administrators group, enlisting target servers to master servers may fail.</span></span> <span data-ttu-id="985f7-105">その場合は、次のエラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="985f7-105">If it does, the following error message is returned:</span></span>  
  
     <span data-ttu-id="985f7-106">"参加操作に失敗しました"</span><span class="sxs-lookup"><span data-stu-id="985f7-106">"The enlistment operation failed."</span></span>  
  
     <span data-ttu-id="985f7-107">この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="985f7-107">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent services to resolve this issue.</span></span>  
  
-   <span data-ttu-id="985f7-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスがローカル システム アカウントで実行されるとき、マスター サーバーとターゲット サーバー間の操作は、同じコンピューターにマスター サーバーとターゲット サーバーの両方が存在する場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="985f7-108">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service is run under the Local System account, master server-target server operations are supported only if both the master server and the target server reside on the same computer.</span></span> <span data-ttu-id="985f7-109">この構成を使用している場合に、ターゲット サーバーをマスター サーバーに参加させると、次のメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="985f7-109">If you use this configuration, the following message is returned when you enlist target servers to a master server:</span></span>  
  
     <span data-ttu-id="985f7-110">"*<target_server_computer_name>* のエージェント開始アカウントに対象サーバーとしてのログオン権限があることを確認します"</span><span class="sxs-lookup"><span data-stu-id="985f7-110">"Ensure the agent start-up account for *<target_server_computer_name>* has rights to log on as targetServer."</span></span>  
  
     <span data-ttu-id="985f7-111">情報提供を目的としたこのメッセージは無視できます。</span><span class="sxs-lookup"><span data-stu-id="985f7-111">You can ignore this informational message.</span></span> <span data-ttu-id="985f7-112">参加操作は、正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="985f7-112">The enlistment operation should complete successfully.</span></span>  
  
 <span data-ttu-id="985f7-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスのアカウントの選択の詳細については、「 [SQL Server エージェント サービスのアカウントの選択](select-an-account-for-the-sql-server-agent-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985f7-113">For more information about choosing an account for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service, see [Select an Account for the SQL Server Agent Service](select-an-account-for-the-sql-server-agent-service.md).</span></span>  
  
  
