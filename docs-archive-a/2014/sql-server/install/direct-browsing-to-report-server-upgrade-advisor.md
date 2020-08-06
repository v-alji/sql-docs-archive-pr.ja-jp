---
title: レポートサーバーへの直接参照 (アップグレードアドバイザー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 3d2814a4-318a-45ed-b093-1e852fab561f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ab4d146bba4bd87de56b30ad100b57f79eb68de3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645369"
---
# <a name="direct-browsing-to-report-server-upgrade-advisor"></a><span data-ttu-id="a3e95-102">レポート サーバーの直接参照 (アップグレード アドバイザー)</span><span class="sxs-lookup"><span data-stu-id="a3e95-102">Direct Browsing to Report Server (Upgrade Advisor)</span></span>
  <span data-ttu-id="a3e95-103">アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリを直接参照していることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="a3e95-103">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory.</span></span>  
  
||  
|-|  
|<span data-ttu-id="a3e95-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]SharePoint モード。</span><span class="sxs-lookup"><span data-stu-id="a3e95-104">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span>|  
  
## <a name="component"></a><span data-ttu-id="a3e95-105">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a3e95-105">Component</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a><span data-ttu-id="a3e95-106">説明</span><span class="sxs-lookup"><span data-stu-id="a3e95-106">Description</span></span>  
 <span data-ttu-id="a3e95-107">アップグレードアドバイザーによって、の現在のインストール [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がレポートサーバーの仮想ディレクトリ ( **http:// \<server name> /ReportServer**など) を直接参照していることが検出されました。</span><span class="sxs-lookup"><span data-stu-id="a3e95-107">Upgrade Advisor detected your current installation of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is browsing directly to the report server virtual directory, for example **http://\<server name>/ReportServer**.</span></span> <span data-ttu-id="a3e95-108">このような直接参照は現在のバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a3e95-108">This is not supported in current versions of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3e95-109">この規則は警告であり、アップグレードはブロックされません。</span><span class="sxs-lookup"><span data-stu-id="a3e95-109">This rule is a warning and upgrade is not blocked.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="a3e95-110">修正措置</span><span class="sxs-lookup"><span data-stu-id="a3e95-110">Corrective Action</span></span>  
 <span data-ttu-id="a3e95-111">ドキュメントライブラリの SharePoint ユーザーインターフェイスを使用して参照するか、 **http:// \<server name> /SharePoint サイト>/_vti_bin/reportserver**を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3e95-111">Browse using the SharePoint user interface for document libraries or use **http://\<server name>/sharepoint site>/_vti_bin/reportserver**.</span></span>  
  
  
