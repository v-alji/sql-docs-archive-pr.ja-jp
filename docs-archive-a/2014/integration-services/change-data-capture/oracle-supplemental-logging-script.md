---
title: Oracle の補足ログ スクリプト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5e6ee618-b89b-46c7-92ad-4fc5ef7b777a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0aa55e71c17574eba9e25e098a3881b0eb4c9e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712261"
---
# <a name="oracle-supplemental-logging-script"></a><span data-ttu-id="8359d-102">Oracle の補足ログ スクリプト</span><span class="sxs-lookup"><span data-stu-id="8359d-102">Oracle Supplemental Logging Script</span></span>
  <span data-ttu-id="8359d-103">このダイアログ ボックスには、Oracle の補足ログ スクリプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8359d-103">This dialog box shows the script the Oracle supplemental logging script.</span></span>  
  
 <span data-ttu-id="8359d-104">CDC インスタンスを使用に備えて準備すると、CDC デザイナーにより、キャプチャするテーブル用の補足ログを設定する Oracle SQL スクリプトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8359d-104">When you prepare a CDC Instance for use, the CDC Designer creates an Oracle SQL script that sets up supplemental logging for the tables to be captured.</span></span> <span data-ttu-id="8359d-105">補足ログ スクリプトは Oracle に対し、特定のテーブルが更新された場合、トランザクション ログに書き込む変更レコードに、変更された列だけでなく、対象のすべての列のデータを含める必要があることを伝えます。</span><span class="sxs-lookup"><span data-stu-id="8359d-105">The supplemental logging script tells Oracle that when a specific table is updated, the change records it writes to the transaction log should contain the data of all columns of interest, not just the columns that changed.</span></span>  
  
 <span data-ttu-id="8359d-106">組織の Oracle DBA ポリシーによっては、補足ログ スクリプトを実行するために、Oracle DBA による確認と承認が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="8359d-106">Depending on the Oracle DBA policies in your organization, running the supplemental logging script may require a review and approval by an Oracle DBA.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8359d-107">オプション</span><span class="sxs-lookup"><span data-stu-id="8359d-107">Options</span></span>  
 <span data-ttu-id="8359d-108">スクリプトの実行方法について使用可能なオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8359d-108">The following are the available options for how to execute the script.</span></span>  
  
 <span data-ttu-id="8359d-109">**スクリプトを実行**</span><span class="sxs-lookup"><span data-stu-id="8359d-109">**Run Script**</span></span>  
 <span data-ttu-id="8359d-110">CDC インスタンスに定義されているテーブルで補足ログ スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="8359d-110">Runs the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="8359d-111">このスクリプトを実行するには、キャプチャするすべてのテーブルに対する ALTER TABLE 権限と、DBA_LOG_GROUPS ビューに対する SELECT 権限が Oracle ユーザーに必要です。</span><span class="sxs-lookup"><span data-stu-id="8359d-111">To run this script, the Oracle user must have ALTER TABLE permission for all the tables to be captured and SELECT permission on the DBA_LOG_GROUPS view.</span></span> <span data-ttu-id="8359d-112">さらに、必要な権限と共に使用する Oracle データベースの資格情報が Oracle ユーザーに必要です。</span><span class="sxs-lookup"><span data-stu-id="8359d-112">In addition, the Oracle user must have the credentials for an Oracle database use with the required permissions.</span></span> <span data-ttu-id="8359d-113">プログラムに Oracle 資格情報を要求させ、スクリプトを実行させることができます。</span><span class="sxs-lookup"><span data-stu-id="8359d-113">You can let the program prompt you for the Oracle credentials and then have it run the script.</span></span>  
  
 <span data-ttu-id="8359d-114">**[名前を付けて保存]**</span><span class="sxs-lookup"><span data-stu-id="8359d-114">**Save As**</span></span>  
 <span data-ttu-id="8359d-115">スクリプトをテキスト ファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="8359d-115">Saves the script to a text file.</span></span> <span data-ttu-id="8359d-116">このオプションは、Oracle データベース管理者 (DBA) が補足ログ スクリプトを調べて実行する必要がある場合に使用されます。ユーザーはスクリプトをテキスト ファイルに保存し、そのテキスト ファイルを後で Oracle DBA に電子メールまたはその他の方法で送信して実行してもらうことができます (SQL\*Plus Oracle ユーティリティまたは Oracle データベースでスクリプトを実行するためのその他のツールを使用)。</span><span class="sxs-lookup"><span data-stu-id="8359d-116">This is used if an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script, the program lets you save the script to a text file that you can later send to the Oracle DBA by email or by other means to be execute later (by using the SQL\*Plus Oracle utility or other tool for running scripts on an Oracle database).</span></span>  
  
 <span data-ttu-id="8359d-117">**Copy** に設定する必要があります</span><span class="sxs-lookup"><span data-stu-id="8359d-117">**Copy**</span></span>  
 <span data-ttu-id="8359d-118">スクリプトをクリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="8359d-118">Copies the script to the clipboard.</span></span> <span data-ttu-id="8359d-119">Oracle 管理者 (DBA) が補足ログ スクリプトを調べて実行する必要がある場合は、必要な場所にスクリプトを貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="8359d-119">When ready you can paste the script in any location you need in case an Oracle database administrator (DBA) needs to examine and execute the supplemental logging script.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8359d-120">参照</span><span class="sxs-lookup"><span data-stu-id="8359d-120">See Also</span></span>  
 <span data-ttu-id="8359d-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span><span class="sxs-lookup"><span data-stu-id="8359d-121">[How to Manage a CDC Instance](manage-a-cdc-instance.md) </span></span>  
 [<span data-ttu-id="8359d-122">CDC インスタンスの管理</span><span class="sxs-lookup"><span data-stu-id="8359d-122">Manage a CDC Instance</span></span>](manage-a-cdc-instance.md)  
  
  
