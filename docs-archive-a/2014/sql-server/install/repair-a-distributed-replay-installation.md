---
title: 分散再生のインストールを修復する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6fcd8ca8-1ceb-457d-9545-096c74e274d7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 57f5b2bde308e48dbf14b52a8b159b30f6a98bc8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643106"
---
# <a name="repair-a-distributed-replay-installation"></a><span data-ttu-id="01dbc-102">分散再生のインストールの修復</span><span class="sxs-lookup"><span data-stu-id="01dbc-102">Repair a Distributed Replay Installation</span></span>
  <span data-ttu-id="01dbc-103">分散再生コンポーネント (コントローラーまたはクライアント) を修復すると、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="01dbc-103">Repairing a Distributed Replay component (controller or client) will do the following:</span></span>  
  
1.  <span data-ttu-id="01dbc-104">ディスク上に関連付けられたすべてのファイルを再インストールし、既存のファイルを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="01dbc-104">Install all associated files on disk again, and replace any existing files.</span></span>  
  
2.  <span data-ttu-id="01dbc-105">対応するサービス アカウントが削除された場合、Windows サービス アカウントを再作成します。</span><span class="sxs-lookup"><span data-stu-id="01dbc-105">Recreate the Windows service account if the corresponding service account was removed.</span></span>  
  
 <span data-ttu-id="01dbc-106">修復操作を利用してコンポーネントを追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="01dbc-106">You cannot use the Repair operation to add or remove components.</span></span> <span data-ttu-id="01dbc-107">コンポーネントを追加または削除するには、セットアップの [**機能の選択**] ページにある機能ツリーで、対応するコンポーネントをオンまたはオフにし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="01dbc-107">To add or remove components, check or uncheck the corresponding component in the Feature tree on the **Feature Selection** page in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
### <a name="to-repair-a-failed-installation-of-distributed-replay"></a><span data-ttu-id="01dbc-108">分散再生のインストールの失敗を修復するには</span><span class="sxs-lookup"><span data-stu-id="01dbc-108">To repair a failed installation of Distributed Replay</span></span>  
  
1.  <span data-ttu-id="01dbc-109">[**スタート**] メニューの [**コントロールパネル**] をクリックし、[**プログラムの追加と削除**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="01dbc-109">From the **Start** menu, click **Control Panel**, and then double-click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="01dbc-110">[ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] プログラムの**アンインストールまたは変更**] ウィンドウでを選択し、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ダイアログボックスで [**修復**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01dbc-110">Select [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in the **Uninstall or change a program** window, and then in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dialog box, click **Repair**.</span></span>  
  
3.  <span data-ttu-id="01dbc-111">ウィザードの手順に従い、[ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] **機能の選択**] ページで、修復する分散再生コンポーネントを選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="01dbc-111">Follow the steps in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wizard, and on the **Select Features** page, select the Distributed Replay components you want to repair, and then click **Next.**.</span></span>  
  
4.  <span data-ttu-id="01dbc-112">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] インストール ウィザードを完了すると、選択した 分散再生の機能が修復されます。</span><span class="sxs-lookup"><span data-stu-id="01dbc-112">Complete the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Installation Wizard to repair the selected Distributed Replay features.</span></span>  
  
  
