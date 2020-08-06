---
title: アップグレードアドバイザーをインストールしています |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- Upgrade Advisor [SQL Server], installing
ms.assetid: 1b7d6eca-1df1-47df-bbba-0fc485706a95
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 40f214b01f3e2066708a060c5f3ad1e8aa4a0a23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713726"
---
# <a name="installing-upgrade-advisor"></a><span data-ttu-id="cb952-102">アップグレード アドバイザーのインストール</span><span class="sxs-lookup"><span data-stu-id="cb952-102">Installing Upgrade Advisor</span></span>
  <span data-ttu-id="cb952-103">SQL Server 2014 Upgrade Advisor のインストール場所は、分析する内容によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cb952-103">Where you install SQL Server 2014 Upgrade Advisor depends on what you will be analyzing.</span></span> <span data-ttu-id="cb952-104">アップグレード アドバイザーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のすべての [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントをリモートで分析できます。</span><span class="sxs-lookup"><span data-stu-id="cb952-104">Upgrade Advisor supports remote analysis of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="cb952-105">のインスタンスをスキャンしない場合は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に接続できる任意のコンピューターにアップグレードアドバイザーをインストールでき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。また、[アップグレードアドバイザーの前提条件](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb952-105">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and that meets the [Upgrade Advisor Prerequisites](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md).</span></span> <span data-ttu-id="cb952-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cb952-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="cb952-107">**SQLUA.msi**ファイルを実行して、アップグレードアドバイザーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="cb952-107">Run the **SQLUA.msi** file to install Upgrade Advisor.</span></span> <span data-ttu-id="cb952-108">コマンド プロンプトからインストールすると、自動インストールを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb952-108">You can install from the command prompt for unattended and automated installations.</span></span> <span data-ttu-id="cb952-109">構文と例について[は、「コマンドプロンプトからのアップグレードアドバイザーのインストール](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb952-109">See [Installing Upgrade Advisor from the Command Prompt](../../../2014/sql-server/install/installing-upgrade-advisor-from-the-command-prompt.md) for syntax and examples.</span></span>  
  
 <span data-ttu-id="cb952-110">SQLUA.msi の入手先:</span><span class="sxs-lookup"><span data-stu-id="cb952-110">Get SQLUA.msi:</span></span>  
  
-   <span data-ttu-id="cb952-111">製品メディアの**redist**フォルダー内 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="cb952-111">In the **redist** folder of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] product media.</span></span>  
  
-   <span data-ttu-id="cb952-112">[SQL 2014 Feature Pack のダウンロード](https://www.microsoft.com/download/details.aspx?id=42295)の一部として。</span><span class="sxs-lookup"><span data-stu-id="cb952-112">As part of the [SQL 2014 Feature Pack download](https://www.microsoft.com/download/details.aspx?id=42295).</span></span>  
  
## <a name="uninstalling-upgrade-advisor"></a><span data-ttu-id="cb952-113">アップグレード アドバイザーのアンインストール</span><span class="sxs-lookup"><span data-stu-id="cb952-113">Uninstalling Upgrade Advisor</span></span>  
 <span data-ttu-id="cb952-114">アップグレードアドバイザーをアンインストールするには、[**プログラムの追加と削除**] を使用します。</span><span class="sxs-lookup"><span data-stu-id="cb952-114">You can uninstall Upgrade Advisor by using **Add or Remove Programs**.</span></span> <span data-ttu-id="cb952-115">コマンド プロンプトの構文でも、削除またはアンインストール操作がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cb952-115">The command prompt syntax also supports removal/uninstall.</span></span>  
  
  
