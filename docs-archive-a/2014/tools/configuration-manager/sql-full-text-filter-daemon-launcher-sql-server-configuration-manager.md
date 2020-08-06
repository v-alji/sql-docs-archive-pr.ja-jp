---
title: SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: d0dc03db-5f76-4558-b041-1ac7b9b5bb16
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45194c893db048151cdb03d33f1419ef42246d69
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631443"
---
# <a name="sql-full-text-filter-daemon-launcher-sql-server-configuration-manager"></a><span data-ttu-id="a2f10-102">SQL フルテキスト フィルター デーモン ランチャー (SQL Server 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="a2f10-102">SQL Full-text Filter Daemon Launcher (SQL Server Configuration Manager)</span></span>
  <span data-ttu-id="a2f10-103">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以降では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フルテキスト検索でフィルター処理や単語区切りを行うフィルター デーモン ホスト プロセスを開始するために、SQL フルテキスト フィルター デーモン ランチャー (FDHOST ランチャー) サービスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2f10-103">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the SQL Full-text Filter Daemon Launcher (FDHOST Launcher) service is used by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] full-text search to start the filter daemon host process, which handles full-text search filtering and word breaking.</span></span> <span data-ttu-id="a2f10-104">フルテキスト検索を使用するには、このサービスが実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2f10-104">This service must be running to use full-text search.</span></span> <span data-ttu-id="a2f10-105">FDHOST ランチャー サービスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の特定のインスタンスに関連付けられているインスタンス対応のサービスです。</span><span class="sxs-lookup"><span data-stu-id="a2f10-105">The FDHOST Launcher service is an instance-aware service that is associated with a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a2f10-106">FDHOST ランチャー サービスにより、開始された各フィルター デーモン ホスト プロセスにサービス アカウント情報が反映されます。</span><span class="sxs-lookup"><span data-stu-id="a2f10-106">The FDHOST Launcher service propagates the service account information to each filter daemon host process started.</span></span> <span data-ttu-id="a2f10-107">フィルター デーモン ホスト プロセスの詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「フルテキスト検索のアーキテクチャ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2f10-107">For information about the filter daemon host processes, see "Full-Text Search Architecture" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
  
