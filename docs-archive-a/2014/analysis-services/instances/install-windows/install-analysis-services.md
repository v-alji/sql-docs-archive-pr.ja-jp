---
title: 表形式モードでの Analysis Services のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
author: minewiskan
ms.author: owend
ms.openlocfilehash: a677fd7770f646067cafb8fedf6d3705ccf2de3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713605"
---
# <a name="install-analysis-services-in-tabular-mode"></a><span data-ttu-id="e97f4-102">表形式モードでの Analysis Services のインストール</span><span class="sxs-lookup"><span data-stu-id="e97f4-102">Install Analysis Services in Tabular Mode</span></span>
  <span data-ttu-id="e97f4-103">新しい表形式のモデリング機能を使用して Analysis Services をインストールする場合、この種類のモデルを使用できるサーバー モードで Analysis Services をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-103">If you are installing Analysis Services to use the new tabular modeling features, you must install Analysis Services in a server mode that supports that type of model.</span></span> <span data-ttu-id="e97f4-104">そのサーバー モードは "表形式" であり、インストール時に構成されます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-104">The server mode is Tabular, and it is configured during installation.</span></span>  
  
 <span data-ttu-id="e97f4-105">このモードでサーバーをインストールすると、表形式モデル デザイナーで作成したホスト ソリューションで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-105">After you install the server in this mode, you can use it host solutions that you build in tabular model designer.</span></span> <span data-ttu-id="e97f4-106">ネットワーク上で表形式のモデル データにアクセスする場合は、表形式モードのサーバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="e97f4-106">A tabular mode server is required if you want tabular model data access over the network.</span></span>  
  
 <span data-ttu-id="e97f4-107">表形式モードは、インストール ウィザードまたはコマンド ライン セットアップで指定できます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-107">You can specify Tabular mode in the Installation Wizard or in a command line setup.</span></span> <span data-ttu-id="e97f4-108">次のセクションでは、各方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e97f4-108">The following sections describe each approach.</span></span>  
  
## <a name="installation-wizard"></a><span data-ttu-id="e97f4-109">インストール ウィザード</span><span class="sxs-lookup"><span data-stu-id="e97f4-109">Installation Wizard</span></span>  
 <span data-ttu-id="e97f4-110">Analysis Services を表形式モードでインストールする場合に使用する SQL Server インストール ウィザードのページを次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="e97f4-110">The following list shows you which pages in the SQL Server Installation wizard are used to install Analysis Services in Tabular mode:</span></span>  
  
1.  <span data-ttu-id="e97f4-111">セットアップの機能ツリーで **[Analysis Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e97f4-111">Select **Analysis Services** from the Feature Tree in Setup.</span></span>  
  
     <span data-ttu-id="e97f4-112">![Analysis Services を示すセットアップの機能ツリー](../../../sql-server/install/media/ssas-setupas.gif "Analysis Services を示すセットアップの機能ツリー")</span><span class="sxs-lookup"><span data-stu-id="e97f4-112">![Setup feature tree showing Analsyis Services](../../../sql-server/install/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")</span></span>  
  
2.  <span data-ttu-id="e97f4-113">[Analysis Services の構成] ページで、[**表形式モード**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e97f4-113">On the Analysis Services Configuration page, be sure to select **Tabular Mode**.</span></span>  
  
     <span data-ttu-id="e97f4-114">![セットアップ ページと Analysis Services 構成オプション](../../../sql-server/install/media/ssas-setupasconfig.gif "セットアップ ページと Analysis Services 構成オプション")</span><span class="sxs-lookup"><span data-stu-id="e97f4-114">![Setup page with Analysis Services config options](../../../sql-server/install/media/ssas-setupasconfig.gif "Setup page with Analysis Services config options")</span></span>  
  
 <span data-ttu-id="e97f4-115">表形式モードでは xVelocity メモリ内分析エンジン (VertiPaq) を使用します。このエンジンは Analysis Services に配置するテーブル モデルの既定のストレージです。</span><span class="sxs-lookup"><span data-stu-id="e97f4-115">Tabular mode uses the xVelocity in-memory analytics engine (VertiPaq), which is the default storage for tabular models that you deploy to Analysis Services.</span></span> <span data-ttu-id="e97f4-116">サーバーにテーブル モデル ソリューションを配置すると、表形式ソリューションを構成する際に、メモリ負荷の高いストレージの代わりに DirectQuery ディスク ストレージを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-116">After you deploy tabular model solutions to the server, you can selectively configure tabular solutions to use DirectQuery disk storage as an alternative to memory-bound storage.</span></span>  
  
## <a name="command-line-setup"></a><span data-ttu-id="e97f4-117">コマンド ライン セットアップ</span><span class="sxs-lookup"><span data-stu-id="e97f4-117">Command Line Setup</span></span>  
 <span data-ttu-id="e97f4-118">SQL Server セットアップにはサーバー モードを指定する新しいパラメーター (`ASSERVERMODE`) があります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-118">SQL Server Setup includes a new parameter (`ASSERVERMODE`) that specifies the server mode.</span></span> <span data-ttu-id="e97f4-119">次の例は、Analysis Services を表形式サーバー モードでインストールするコマンド ライン セットアップを示しています。</span><span class="sxs-lookup"><span data-stu-id="e97f4-119">The following example illustrates a command line setup that installs Analysis Services in Tabular server mode.</span></span>  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="e97f4-120">`INSTANCENAME` は 17 文字未満にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-120">`INSTANCENAME` must be less than 17 characters.</span></span>  
  
 <span data-ttu-id="e97f4-121">プレースホルダー アカウント値はすべて、有効なアカウントおよびパスワードに置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-121">All placeholder account values must be replaced with valid accounts and password.</span></span>  
  
 <span data-ttu-id="e97f4-122">SQL Server Management Studio や [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] などのツールは、提供されているコマンド ライン構文の例ではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="e97f4-122">Tools such as SQL Server Management Studio or [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] are not installed using the example command line syntax that is provided.</span></span> <span data-ttu-id="e97f4-123">機能の追加の詳細については、「 [Install SQL Server 2014 from The Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e97f4-123">For more information about adding features, see [Install SQL Server 2014 from the Command Prompt](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).</span></span>  
  
 <span data-ttu-id="e97f4-124">`ASSERVERMODE` では、大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-124">`ASSERVERMODE` is case-sensitive.</span></span>  <span data-ttu-id="e97f4-125">値はすべて大文字で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-125">All values must be expressed in upper case.</span></span> <span data-ttu-id="e97f4-126">次の表に、`ASSERVERMODE` の有効な値を示します。</span><span class="sxs-lookup"><span data-stu-id="e97f4-126">The following table describes the valid values for `ASSERVERMODE`.</span></span>  
  
|<span data-ttu-id="e97f4-127">値</span><span class="sxs-lookup"><span data-stu-id="e97f4-127">Value</span></span>|<span data-ttu-id="e97f4-128">説明</span><span class="sxs-lookup"><span data-stu-id="e97f4-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e97f4-129">MULTIDIMENSIONAL</span><span class="sxs-lookup"><span data-stu-id="e97f4-129">MULTIDIMENSIONAL</span></span>|<span data-ttu-id="e97f4-130">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="e97f4-130">This is the default value.</span></span> <span data-ttu-id="e97f4-131">`ASSERVERMODE` を設定しない場合、サーバーは多次元サーバー モードでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e97f4-131">If you do not set `ASSERVERMODE`, the server is installed in Multidimensional server mode.</span></span>|  
|<span data-ttu-id="e97f4-132">POWERPIVOT</span><span class="sxs-lookup"><span data-stu-id="e97f4-132">POWERPIVOT</span></span>|<span data-ttu-id="e97f4-133">この値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e97f4-133">This value is optional.</span></span> <span data-ttu-id="e97f4-134">実際には、`ROLE` パラメーターを設定した場合、サーバー モードは自動的に 1 に設定され、SharePoint のインストール時に PowerPivot の `ASSERVERMODE` が省略可能になります。</span><span class="sxs-lookup"><span data-stu-id="e97f4-134">In practice, if you set the `ROLE` parameter, the server mode is automatically set to 1, making `ASSERVERMODE` optional for a PowerPivot for SharePoint installation.</span></span> <span data-ttu-id="e97f4-135">詳細については、「[コマンドプロンプトからの PowerPivot のインストール](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e97f4-135">For more information, see [Install PowerPivot from the Command Prompt](../../../sql-server/install/install-powerpivot-from-the-command-prompt.md).</span></span>|  
|<span data-ttu-id="e97f4-136">TABULAR</span><span class="sxs-lookup"><span data-stu-id="e97f4-136">TABULAR</span></span>|<span data-ttu-id="e97f4-137">コマンド ライン セットアップを使用して Analysis Services を表形式モードでインストールする場合、この値は必須です。</span><span class="sxs-lookup"><span data-stu-id="e97f4-137">This value is required if you are installing Analysis Services in Tabular mode using command line setup.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e97f4-138">参照</span><span class="sxs-lookup"><span data-stu-id="e97f4-138">See Also</span></span>  
 <span data-ttu-id="e97f4-139">[Analysis Services インスタンスのサーバーモードの決定](../determine-the-server-mode-of-an-analysis-services-instance.md) </span><span class="sxs-lookup"><span data-stu-id="e97f4-139">[Determine the Server Mode of an Analysis Services Instance](../determine-the-server-mode-of-an-analysis-services-instance.md) </span></span>  
 <span data-ttu-id="e97f4-140">[テーブルモデルデータベースに対するメモリ内または DirectQuery アクセスの構成](../../tabular-models/enable-directquery-mode-in-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="e97f4-140">[Configure In-Memory or DirectQuery Access for a Tabular Model Database](../../tabular-models/enable-directquery-mode-in-ssms.md) </span></span>  
 [<span data-ttu-id="e97f4-141">SSAS 表形式&#41;の表形式モデル &#40;</span><span class="sxs-lookup"><span data-stu-id="e97f4-141">Tabular Modeling &#40;SSAS Tabular&#41;</span></span>](../../tabular-models/tabular-models-ssas.md)  
  
  
