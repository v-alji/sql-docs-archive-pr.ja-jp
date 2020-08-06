---
title: '[サーバーへの接続] ([接続プロパティ] ページ) Analysis Services | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttoas.connectionproperties.f1
ms.assetid: 26cf53e3-3bcb-4697-8a88-53e93bc68b56
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 04706671ea8b0a50f2bf72cd7b73db88dce34d89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711018"
---
# <a name="connect-to-server-connection-properties-page-analysis-services"></a><span data-ttu-id="52fc6-102">[サーバーへの接続] ([接続プロパティ] ページ) Analysis Services</span><span class="sxs-lookup"><span data-stu-id="52fc6-102">Connect to Server (Connection Properties Page) Analysis Services</span></span>
  <span data-ttu-id="52fc6-103">このタブを使用して、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssAS](../includes/ssas-md.md)] **登録済みサーバー**に接続または登録するときのオプションを表示または指定します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] or registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="52fc6-104">接続時には、**[接続]** および **[オプション]** のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52fc6-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="52fc6-105">**を登録するときには、** [テスト] **および** [保存] [!INCLUDE[ssAS](../includes/ssas-md.md)]のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52fc6-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssAS](../includes/ssas-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="52fc6-106">Options</span><span class="sxs-lookup"><span data-stu-id="52fc6-106">Options</span></span>  
 <span data-ttu-id="52fc6-107">**データベースへの接続**</span><span class="sxs-lookup"><span data-stu-id="52fc6-107">**Connect to database**</span></span>  
 <span data-ttu-id="52fc6-108">接続するデータベースを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-108">Select a database to connect to from the list.</span></span> <span data-ttu-id="52fc6-109">を選択した場合は、 **\<default>** サーバーの既定のデータベースに接続されます。</span><span class="sxs-lookup"><span data-stu-id="52fc6-109">If you select **\<default>**, you will be connected to the default database for the server.</span></span> <span data-ttu-id="52fc6-110">を選択した場合は、 **\<Browse server>** 接続先のデータベースのサーバーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="52fc6-110">If you select **\<Browse server>**, you can browse the server for the database you would like to connect to.</span></span>  
  
 <span data-ttu-id="52fc6-111">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="52fc6-111">**Connection timeout**</span></span>  
 <span data-ttu-id="52fc6-112">接続が確立されるまで待機する秒数を入力します。この時間が経過するとタイムアウトになります。既定値は15秒です。</span><span class="sxs-lookup"><span data-stu-id="52fc6-112">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="52fc6-113">**実行タイムアウト**</span><span class="sxs-lookup"><span data-stu-id="52fc6-113">**Execution timeout**</span></span>  
 <span data-ttu-id="52fc6-114">タスクの実行がサーバーで完了するまで待機する秒数を入力します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-114">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="52fc6-115">既定値は 0 秒です。つまり、タイムアウトはありません。</span><span class="sxs-lookup"><span data-stu-id="52fc6-115">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="52fc6-116">**接続を暗号化する**</span><span class="sxs-lookup"><span data-stu-id="52fc6-116">**Encrypt connection**</span></span>  
 <span data-ttu-id="52fc6-117">接続の暗号化を強制します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-117">Forces encryption of the connection.</span></span>  
  
 <span data-ttu-id="52fc6-118">**[すべてリセット]**</span><span class="sxs-lookup"><span data-stu-id="52fc6-118">**Reset All**</span></span>  
 <span data-ttu-id="52fc6-119">手動で入力された接続プロパティ値をすべて既定値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="52fc6-119">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="52fc6-120">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="52fc6-120">**Connect**</span></span>  
 <span data-ttu-id="52fc6-121">一覧表示された値を使用して接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-121">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="52fc6-122">**Options**</span><span class="sxs-lookup"><span data-stu-id="52fc6-122">**Options**</span></span>  
 <span data-ttu-id="52fc6-123">クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="52fc6-123">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="52fc6-124">**テスト**</span><span class="sxs-lookup"><span data-stu-id="52fc6-124">**Test**</span></span>  
 <span data-ttu-id="52fc6-125">[!INCLUDE[ssAS](../includes/ssas-md.md)] を **登録済みサーバー**に登録するときに、クリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="52fc6-125">When registering [!INCLUDE[ssAS](../includes/ssas-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="52fc6-126">**および**</span><span class="sxs-lookup"><span data-stu-id="52fc6-126">**Save**</span></span>  
 <span data-ttu-id="52fc6-127">**登録済みサーバー**に設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="52fc6-127">Saves the settings in **Registered Servers**.</span></span>  
  
  
