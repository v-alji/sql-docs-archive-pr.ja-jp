---
title: SQL Server のインストールの検証 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8dd4e6ce7800c3a0a9db51f6c1a4bddfe7a188c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714562"
---
# <a name="validate-a-sql-server-installation"></a><span data-ttu-id="2dc95-102">SQL Server のインストールの検証</span><span class="sxs-lookup"><span data-stu-id="2dc95-102">Validate a SQL Server Installation</span></span>
  <span data-ttu-id="2dc95-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の検出レポートは、コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョンおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を確認するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report can be used to verify the version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features installed on the computer.</span></span> <span data-ttu-id="2dc95-104">**インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート**には、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] ローカルサーバーにインストールされている、、、、、およびの各製品と機能のレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-104">The **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report** displays a report of all [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], and [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] products and features that are installed on the local server.</span></span> <span data-ttu-id="2dc95-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートは、 **インストール センターの** [ツール] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページで利用できます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report is available on the **Tools** page on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center.</span></span>  
  
 <span data-ttu-id="2dc95-106">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには**</span><span class="sxs-lookup"><span data-stu-id="2dc95-106">**To run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report:**</span></span>  
  
 <span data-ttu-id="2dc95-107">**[スタート]** メニューを使用し、 **[すべてのプログラム]** 、 **[[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>]** 、 **[構成ツール]** の順にポイントし、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** をクリックして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センターを起動します。</span><span class="sxs-lookup"><span data-stu-id="2dc95-107">Launch the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation center, using the **Start** menu, point to **All Programs**, point to **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>**, point to **Configuration Tools**, and click **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**.</span></span> <span data-ttu-id="2dc95-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポートを実行するには、 **[[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール センター]** の左側のナビゲーション領域にある **[ツール]** をクリックし、 **[インストール済み [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能の検出レポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2dc95-108">To run the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report, click **Tools** in the left-hand navigation area of **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Center**, and then click **Installed [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features discovery report**.</span></span>  
  
 <span data-ttu-id="2dc95-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]検出レポートは、% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<最後のセットアップセッションに保存され \> ます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-109">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] discovery report is saved to %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
 <span data-ttu-id="2dc95-110">また、コマンド ラインから検出レポートを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-110">You can also generate the discovery report through the command line.</span></span> <span data-ttu-id="2dc95-111">コマンドプロンプトから "Setup.exe/Action = rundiscovery" を実行します。上記のコマンドラインに "/q" を追加すると、UI は表示されませんが、レポートは% ProgramFiles% \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \120\Setup Bootstrap\Log \\<最後のセットアップセッションで作成され \> ます。</span><span class="sxs-lookup"><span data-stu-id="2dc95-111">Run "Setup.exe /Action=RunDiscovery" from a command prompt If you add "/q" to the command line above no UI will be shown, but the report will still be created in %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\120\Setup Bootstrap\Log\\<last Setup Session\>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc95-112">参照</span><span class="sxs-lookup"><span data-stu-id="2dc95-112">See Also</span></span>  
 [<span data-ttu-id="2dc95-113">SQL Server セットアップ ログ ファイルの表示と読み取り</span><span class="sxs-lookup"><span data-stu-id="2dc95-113">View and Read SQL Server Setup Log Files</span></span>](view-and-read-sql-server-setup-log-files.md)  
  
  
