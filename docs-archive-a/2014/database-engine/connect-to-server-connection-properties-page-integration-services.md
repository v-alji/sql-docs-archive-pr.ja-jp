---
title: '[サーバーへの接続] ([接続プロパティ] ページ) Integration Services |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodts.connectionproperties.f1
- sql12.ssiseditserverregistration.connectionproperties.f1
ms.assetid: c2513dab-8415-4e0c-9475-6d4ab97fea7c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 05f3d370a3f3a299bb90df53538b3fa3e90e28c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740375"
---
# <a name="connect-to-server-connection-properties-page-integration-services"></a><span data-ttu-id="559cf-102">[サーバーへの接続] ([接続プロパティ] ページ) (Integration Services)</span><span class="sxs-lookup"><span data-stu-id="559cf-102">Connect to Server (Connection Properties Page) Integration Services</span></span>
  <span data-ttu-id="559cf-103">このタブを使用して、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[ssIS](../includes/ssis-md.md)] **登録済みサーバー**に接続または登録するときのオプションを表示または指定します。</span><span class="sxs-lookup"><span data-stu-id="559cf-103">Use this tab to view or specify options when connecting to [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] or registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**.</span></span> <span data-ttu-id="559cf-104">接続時には、**[接続]** および **[オプション]** のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="559cf-104">**Connect** and **Options** only appear in this dialog box when connecting.</span></span> <span data-ttu-id="559cf-105">**を登録するときには、** [テスト] **および** [保存] [!INCLUDE[ssIS](../includes/ssis-md.md)]のみがこのダイアログ ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="559cf-105">**Test** and **Save** only appear in this dialog box when registering [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
## <a name="options"></a><span data-ttu-id="559cf-106">Options</span><span class="sxs-lookup"><span data-stu-id="559cf-106">Options</span></span>  
 <span data-ttu-id="559cf-107">**ポート番号**</span><span class="sxs-lookup"><span data-stu-id="559cf-107">**Port number**</span></span>  
 <span data-ttu-id="559cf-108">[!INCLUDE[ssIS](../includes/ssis-md.md)]によって使用されるポート番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="559cf-108">Enter the port number used by [!INCLUDE[ssIS](../includes/ssis-md.md)].</span></span>  
  
 <span data-ttu-id="559cf-109">**接続のタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="559cf-109">**Connection time-out**</span></span>  
 <span data-ttu-id="559cf-110">接続が確立されるまで待機する秒数を入力します。この時間が経過するとタイムアウトになります。既定値は15秒です。</span><span class="sxs-lookup"><span data-stu-id="559cf-110">Enter the number of seconds to wait for a connection to be established before timing out. The default value is 15 seconds.</span></span>  
  
 <span data-ttu-id="559cf-111">**[実行タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="559cf-111">**Execution time-out**</span></span>  
 <span data-ttu-id="559cf-112">タスクの実行がサーバーで完了するまで待機する秒数を入力します。</span><span class="sxs-lookup"><span data-stu-id="559cf-112">Enter the amount of time in seconds to wait before execution of a task is completed on the server.</span></span> <span data-ttu-id="559cf-113">既定値は 0 秒です。つまり、タイムアウトはありません。</span><span class="sxs-lookup"><span data-stu-id="559cf-113">The default value is zero seconds, which indicates there is no time-out.</span></span>  
  
 <span data-ttu-id="559cf-114">**[すべてリセット]**</span><span class="sxs-lookup"><span data-stu-id="559cf-114">**Reset All**</span></span>  
 <span data-ttu-id="559cf-115">手動で入力された接続プロパティ値をすべて既定値に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="559cf-115">Replace all manually entered connection property values with the default values.</span></span>  
  
 <span data-ttu-id="559cf-116">**のインスタンスに接続するときには、**</span><span class="sxs-lookup"><span data-stu-id="559cf-116">**Connect**</span></span>  
 <span data-ttu-id="559cf-117">一覧表示された値を使用して接続を試行します。</span><span class="sxs-lookup"><span data-stu-id="559cf-117">Attempt a connection using the listed values.</span></span>  
  
 <span data-ttu-id="559cf-118">**Options**</span><span class="sxs-lookup"><span data-stu-id="559cf-118">**Options**</span></span>  
 <span data-ttu-id="559cf-119">クリックすると、ダイアログが切り替わり、パスワードの保存などの追加のサーバー接続オプションが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="559cf-119">Click to change the dialog and hide the additional server connection options, such as remembering the password.</span></span>  
  
 <span data-ttu-id="559cf-120">**テスト**</span><span class="sxs-lookup"><span data-stu-id="559cf-120">**Test**</span></span>  
 <span data-ttu-id="559cf-121">[!INCLUDE[ssIS](../includes/ssis-md.md)] を **登録済みサーバー**に登録するときに、クリックして接続をテストします。</span><span class="sxs-lookup"><span data-stu-id="559cf-121">When registering [!INCLUDE[ssIS](../includes/ssis-md.md)] in **Registered Servers**, click to test the connection.</span></span>  
  
 <span data-ttu-id="559cf-122">**および**</span><span class="sxs-lookup"><span data-stu-id="559cf-122">**Save**</span></span>  
 <span data-ttu-id="559cf-123">**登録済みサーバー**に設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="559cf-123">Saves the settings in **Registered Servers**.</span></span>  
  
  
