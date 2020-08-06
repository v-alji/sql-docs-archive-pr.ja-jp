---
title: '方法: Upgrade Advisor をインストールする |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3ed5b66522126bfabc94bfa8036ec6c31ac04500
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644808"
---
# <a name="how-to-install-upgrade-advisor"></a><span data-ttu-id="be444-102">アップグレード アドバイザーをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="be444-102">How to: Install Upgrade Advisor</span></span>
  <span data-ttu-id="be444-103">アップグレード アドバイザーでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 以外のサポートされているすべてのコンポーネントをリモートで分析できます。</span><span class="sxs-lookup"><span data-stu-id="be444-103">Upgrade Advisor supports remote analysis of all supported components except [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="be444-104">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンしない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続できる任意のコンピューターにアップグレード アドバイザーをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="be444-104">If you are not scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can install Upgrade Advisor on any computer that can connect to your instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="be444-105">コンピューターはアップグレード アドバイザーの前提条件を満たしている必要もあります。</span><span class="sxs-lookup"><span data-stu-id="be444-105">The computer must also meet Upgrade Advisor prerequisites.</span></span> <span data-ttu-id="be444-106">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンスをスキャンする場合は、アップグレード アドバイザーをレポート サーバーにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be444-106">If you are scanning instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must install Upgrade Advisor on the report server.</span></span>  
  
 <span data-ttu-id="be444-107">詳細については、「 [Upgrade Advisor のインストール](../../../2014/sql-server/install/installing-upgrade-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be444-107">For more information, see [Installing Upgrade Advisor](../../../2014/sql-server/install/installing-upgrade-advisor.md).</span></span>  
  
### <a name="to-install-upgrade-advisor"></a><span data-ttu-id="be444-108">アップグレード アドバイザーをインストールするには</span><span class="sxs-lookup"><span data-stu-id="be444-108">To install Upgrade Advisor</span></span>  
  
1.  <span data-ttu-id="be444-109">次の方法のいずれかを使用してインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="be444-109">Start the installation using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="be444-110">Web サイトからをインストールする場合は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [**ダウンロード**] リンクをクリックし、[**実行**] ボタンをクリックしてインストールを開始します。</span><span class="sxs-lookup"><span data-stu-id="be444-110">If you are installing from the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Web site, click the **Download** link and then click the **Run** button to start the installation.</span></span>  
  
    -   <span data-ttu-id="be444-111">製品メディアからインストールする場合は、 **redist**フォルダーを開き、**アップグレードアドバイザー**フォルダーを開き、[ **SQLUA.msi**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="be444-111">If you are installing from the product media, open the **redist** folder, open the **Upgrade Advisor** folder, and then double-click **SQLUA.msi**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="be444-112">アップグレード アドバイザーを使用するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4 が必要です。</span><span class="sxs-lookup"><span data-stu-id="be444-112">Upgrade Advisor requires the [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4.</span></span> <span data-ttu-id="be444-113">インストールされていない場合やバージョンが古い場合は、エラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="be444-113">If it is not installed, or if you have a pre-release version, an error message will appear.</span></span> <span data-ttu-id="be444-114">古いバージョンの [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] をアンインストールしてから、最新バージョンの .NET Framework 4 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="be444-114">Uninstall any earlier version of the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] and then install the latest version of .NET Framework 4.</span></span>  
    >   
    >  <span data-ttu-id="be444-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom はアップグレードアドバイザーをインストールするための前提条件で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] あり、アップグレードアドバイザーのセットアップではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="be444-115">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="be444-116">セットアップでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Feature Pack から scriptdom をダウンロードしてインストールする必要があり [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="be444-116">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
2.  <span data-ttu-id="be444-117">[ \*\* [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor セットアップの開始**] ページで、[**次へ\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be444-117">On the **Welcome to the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor Setup** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="be444-118">[**使用許諾契約書**] ページで、使用許諾契約書を読みます。</span><span class="sxs-lookup"><span data-stu-id="be444-118">On the **License Agreement** page, read the license agreement.</span></span> <span data-ttu-id="be444-119">同意する場合は、[**使用許諾契約書に同意**します] を選択し、[**次へ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be444-119">If you agree, select **I accept the license agreement** and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="be444-120">[**登録情報**] ページで、名前と会社を入力します。</span><span class="sxs-lookup"><span data-stu-id="be444-120">On the **Registration Information** page, enter your name and company.</span></span>  
  
5.  <span data-ttu-id="be444-121">[**機能の選択**] ページで、[**インストールパス**] の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="be444-121">On the **Feature Selection** page, review the **Installation path** value.</span></span> <span data-ttu-id="be444-122">必要に応じて、[**参照**] ボタンを使用して場所を変更します。</span><span class="sxs-lookup"><span data-stu-id="be444-122">If necessary, use the **Browse** button to change the location.</span></span> <span data-ttu-id="be444-123">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="be444-123">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="be444-124">[**プログラムのインストールの準備完了**] ページで、[**インストール**] をクリックしてアップグレードアドバイザーをインストールします。</span><span class="sxs-lookup"><span data-stu-id="be444-124">On the **Ready to Install the Program** page, click **Install** to install Upgrade Advisor.</span></span>  
  
7.  <span data-ttu-id="be444-125">**[完了]** をクリックして、ウィザードを終了します。</span><span class="sxs-lookup"><span data-stu-id="be444-125">Click **Finish** to exit the wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be444-126">参照</span><span class="sxs-lookup"><span data-stu-id="be444-126">See Also</span></span>  
 [<span data-ttu-id="be444-127">アップグレード アドバイザーの前提条件</span><span class="sxs-lookup"><span data-stu-id="be444-127">Upgrade Advisor Prerequisites</span></span>](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
