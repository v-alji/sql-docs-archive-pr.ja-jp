---
title: 補足ログ スクリプトの生成および実行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- supLog
ms.assetid: 6e940d93-12c6-4cda-9333-5489b245f0e4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1437a4b0f790376268095d8e52afa981af865b44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712309"
---
# <a name="generate-and-run-the-supplemental-logging-script"></a><span data-ttu-id="eee9a-102">補足ログ スクリプトの生成および実行</span><span class="sxs-lookup"><span data-stu-id="eee9a-102">Generate and Run the Supplemental Logging Script</span></span>
  <span data-ttu-id="eee9a-103">補足ログを設定する Oracle ソース データベースでスクリプトを実行するには、[変更をキャプチャするためのテーブルの設定] ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-103">Use the Set up Tables for Capturing Changes page to run a script on the Oracle source database that will set up supplemental logging.</span></span>  
  
 <span data-ttu-id="eee9a-104">**補足ログ スクリプトを実行するには**</span><span class="sxs-lookup"><span data-stu-id="eee9a-104">**To run the supplemental logging scripts**</span></span>  
  
 <span data-ttu-id="eee9a-105">**[スクリプトの実行]** をクリックして、CDC インスタンスに定義されているテーブルで補足ログ スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-105">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="eee9a-106">このスクリプトは、キャプチャされるテーブルに UPDATE 操作のログを記録するときに、必要なすべての列をトランザクション ログに書き込むように Oracle データベースに対して指示します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-106">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="eee9a-107">通常、このスクリプトは Oracle システム管理者によって検査されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="eee9a-107">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
 <span data-ttu-id="eee9a-108">SQL\*Plus を使用してスクリプトを手動で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="eee9a-108">You can also run the scripts manually using SQL \* Plus.</span></span>  
  
 <span data-ttu-id="eee9a-109">**スクリプトを手動で実行するには**</span><span class="sxs-lookup"><span data-stu-id="eee9a-109">**To run the scripts manually**</span></span>  
  
 <span data-ttu-id="eee9a-110">**[コピー]** をクリックしてスクリプトをクリップボードに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="eee9a-110">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="eee9a-111">SQL\*Plus を開き、Oracle ソース データベースのディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-111">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="eee9a-112">SQL\*Plus にスクリプトを貼り付けて実行します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-112">Paste the script into SQL\*Plus to run it.</span></span>  
  
 <span data-ttu-id="eee9a-113">補足ログ スクリプトをテキスト ファイルで保存するには、 **[名前を付けて保存]** をクリックし、ファイルを保存する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-113">To save the supplemental logging script in a text file, click **Save as** and browse to the location where you want to save the file.</span></span> <span data-ttu-id="eee9a-114">ファイルに名前を付け、 **[保存]** をクリックしてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="eee9a-114">Give the file a name and click **Save** to save the file.</span></span>  
  
 <span data-ttu-id="eee9a-115">**[次へ]** をクリックして「 [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="eee9a-115">Click **Next** to [Generate Mirror Tables and CDC Capture Instances](generate-mirror-tables-and-cdc-capture-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee9a-116">参照</span><span class="sxs-lookup"><span data-stu-id="eee9a-116">See Also</span></span>  
 <span data-ttu-id="eee9a-117">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="eee9a-117">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="eee9a-118">補足ログ スクリプトの確認および生成</span><span class="sxs-lookup"><span data-stu-id="eee9a-118">Review and Generate Supplemental Logging Scripts</span></span>](review-and-generate-supplemental-logging-scripts.md)  
  
  
