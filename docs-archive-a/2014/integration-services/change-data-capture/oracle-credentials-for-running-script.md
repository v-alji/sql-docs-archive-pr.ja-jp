---
title: スクリプトを実行するための Oracle 資格情報 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4a301cb0-2f5b-41ba-81bf-46b41d07f137
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 683b313e5b1065c3709c4637ddf968641612cc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712262"
---
# <a name="oracle-credentials-for-running-script"></a><span data-ttu-id="c2b50-102">Oracle Credentials for Running Script</span><span class="sxs-lookup"><span data-stu-id="c2b50-102">Oracle Credentials for Running Script</span></span>
  <span data-ttu-id="c2b50-103">Oracle CDC デザイナー コンソールから Oracle の補足ログ スクリプトを実行するために、スクリプトを実行する Oracle ユーザーの資格情報の入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="c2b50-103">To run the Oracle supplemental logging script from the Oracle CDC Designer console, the program prompts you for the credentials of the Oracle user who is running the script.</span></span> <span data-ttu-id="c2b50-104">このスクリプトを実行するには、キャプチャするすべてのテーブルに対する ALTER TABLE 権限と、DBA_LOG_GROUPS ビューに対する SELECT 権限が Oracle ユーザーに必要です。</span><span class="sxs-lookup"><span data-stu-id="c2b50-104">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="c2b50-105">タスク一覧</span><span class="sxs-lookup"><span data-stu-id="c2b50-105">Task List</span></span>  
 <span data-ttu-id="c2b50-106">このダイアログ ボックスでは次の情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2b50-106">Enter the following in this dialog box:</span></span>  
  
 <span data-ttu-id="c2b50-107">**認証**</span><span class="sxs-lookup"><span data-stu-id="c2b50-107">**Authentication**</span></span>  
  
 <span data-ttu-id="c2b50-108">次のいずれかを選択してください。</span><span class="sxs-lookup"><span data-stu-id="c2b50-108">Select one of the following:</span></span>  
  
-   <span data-ttu-id="c2b50-109">**[Windows 認証]** : 現在の Windows ドメイン資格情報を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="c2b50-109">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="c2b50-110">このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2b50-110">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="c2b50-111">**[Oracle 認証]** : このオプションを選択する場合、接続先のソース Oracle データベースでのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2b50-111">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Source Oracle database you are connecting to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b50-112">参照</span><span class="sxs-lookup"><span data-stu-id="c2b50-112">See Also</span></span>  
 <span data-ttu-id="c2b50-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="c2b50-113">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="c2b50-114">補足ログ スクリプトの確認および生成</span><span class="sxs-lookup"><span data-stu-id="c2b50-114">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
