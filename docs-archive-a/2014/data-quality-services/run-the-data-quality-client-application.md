---
title: Data Quality Client アプリケーションの実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.browseforservers.f1
- sql12.dqs.connecttoserver.f1
ms.assetid: 0b2aa202-7ab2-4c9d-b0f1-802588053a1e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45372ce22fd1b18f0ec13f7a7fd76a369b78dfd6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742610"
---
# <a name="run-the-data-quality-client-application"></a><span data-ttu-id="fb242-102">Data Quality Client アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="fb242-102">Run the Data Quality Client Application</span></span>
  <span data-ttu-id="fb242-103">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] を実行し、[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] にログオンして、[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] (DQS) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="fb242-103">You can use [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by running [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], and logging on to a [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="fb242-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="fb242-104">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="fb242-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="fb242-105">Prerequisites</span></span>  
 <span data-ttu-id="fb242-106">DQSInstaller.exe ファイルを実行して [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] のインストールを完了しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb242-106">You must have completed the [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] installation by running the DQSInstaller.exe file.</span></span> <span data-ttu-id="fb242-107">詳細については、「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fb242-107">For more information, see [Run DQSInstaller.exe to Complete Data Quality Server Installation](install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="fb242-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fb242-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="fb242-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="fb242-109">Permissions</span></span>  
 <span data-ttu-id="fb242-110">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]にログオンするには、DQS_MAIN データベースに対して、3 つの DQS ロール (dqs_administrator、dqs_kb_editor、dqs_kb_operator) のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb242-110">You must have one of the three DQS roles (dqs_adminstrator, dqs_kb_editor, or dqs_kb_operator) granted on the DQS_MAIN database to be able to log on to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)].</span></span>  
  
##  <a name="run-data-quality-client"></a><a name="Run"></a> <span data-ttu-id="fb242-111">Data Quality Client の実行</span><span class="sxs-lookup"><span data-stu-id="fb242-111">Run Data Quality Client</span></span>  
 <span data-ttu-id="fb242-112">インストール済みのコンピューターで [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] を実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb242-112">To run [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] on the computer where you have installed it, proceed as follows:</span></span>  
  
1.  <span data-ttu-id="fb242-113">**[スタート]** ボタンをクリックし、**[すべてのプログラム]** をポイントして、**[[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]]**、**[Data Quality Services]**、**[Data Quality Client]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb242-113">Click **Start**, point to **All Programs**, click **[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]**, click **Data Quality Services**, and then click **Data Quality Client**.</span></span>  
  
2.  <span data-ttu-id="fb242-114">**[サーバーに接続]** ダイアログで次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="fb242-114">In the **Connect to Server** dialog box:</span></span>  
  
    1.  <span data-ttu-id="fb242-115">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションを接続するサーバーを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb242-115">Specify the server that you want to connect the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] application to.</span></span> <span data-ttu-id="fb242-116">**[(ローカル)]** を選択し、ローカル コンピューター上の [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="fb242-116">Select **(LOCAL)** to connect to [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] on the local computer.</span></span> <span data-ttu-id="fb242-117">下矢印をクリックして、 **\<Browse network for more servers>** 別のサーバーに接続する (またはローカルサーバーに名前で接続する) こともできます。</span><span class="sxs-lookup"><span data-stu-id="fb242-117">You can also click the down arrow and select **\<Browse network for more servers>** to connect to a different server (or to connect to the local server by name).</span></span> <span data-ttu-id="fb242-118">**[サーバーの参照]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb242-118">The **Browse for Servers** dialog box will be displayed.</span></span> <span data-ttu-id="fb242-119">**[ローカル サーバー]** タブまたは **[ネットワーク サーバー]** タブでサーバーを選択できます。</span><span class="sxs-lookup"><span data-stu-id="fb242-119">You can select a server in the **Local Servers** tab or in the **Network Servers** tab.</span></span>  
  
    2.  <span data-ttu-id="fb242-120">[!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] と [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] の間のデータ転送を暗号化する場合は、**[オプション]** をクリックし、**[暗号化接続]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="fb242-120">If you want to encrypt data transfer between [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] and [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)], click **Options**, and then select the **Encrypt Connection** check box.</span></span>  
  
3.  <span data-ttu-id="fb242-121">**[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fb242-121">Click **Connect**.</span></span>  
  
 <span data-ttu-id="fb242-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb242-122">The [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen appears.</span></span> <span data-ttu-id="fb242-123">詳細については、「[Data Quality Client のホーム画面](../../2014/data-quality-services/data-quality-client-home-screen.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb242-123">For more information, see [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md).</span></span>  
  
  
