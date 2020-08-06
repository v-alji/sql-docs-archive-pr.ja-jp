---
title: 補足ログ スクリプトの確認および生成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- scripts
ms.assetid: 5c858ae2-37d6-42e8-a252-7f6ed4e628a7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cb735c0ee318ac68d48c71c09fc76ec305eb2552
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634594"
---
# <a name="review-and-generate-supplemental-logging-scripts"></a><span data-ttu-id="19983-102">補足ログ スクリプトの確認および生成</span><span class="sxs-lookup"><span data-stu-id="19983-102">Review and Generate Supplemental Logging Scripts</span></span>
  <span data-ttu-id="19983-103">補足ログを設定する Oracle ソース データベースでスクリプトを実行または再実行するには、 **[スクリプト]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="19983-103">Use the **Scripts** tab to run or re-run a script on the Oracle source database that sets up supplemental logging.</span></span>  
  
 <span data-ttu-id="19983-104">スクリプトを実行する前に、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="19983-104">Before you run the scripts select one of the following:</span></span>  
  
 <span data-ttu-id="19983-105">**[このセッションの変更を含める]**</span><span class="sxs-lookup"><span data-stu-id="19983-105">**Include changes in this session**</span></span>  
 <span data-ttu-id="19983-106">CDC インスタンスに追加された任意の新しいテーブルまたはプロパティ エディターを使用して任意の方法で変更されたテーブルでスクリプトを実行するには、これを選択します。</span><span class="sxs-lookup"><span data-stu-id="19983-106">Select this to run the script on any new table that was added to the CDC instance or on tables that were changed in any way using the Properties editor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19983-107">CDC インスタンスのテーブルが変更されていない場合、Oracle の補足ログ スクリプト領域は空になります。</span><span class="sxs-lookup"><span data-stu-id="19983-107">If no changes were made to the tables in the CDC instance, the Oracle supplemental logging script area will be empty.</span></span>  
  
 <span data-ttu-id="19983-108">**[すべてのテーブルを含める/インスタンスをキャプチャする]**</span><span class="sxs-lookup"><span data-stu-id="19983-108">**Include all tables/capture instances**</span></span>  
 <span data-ttu-id="19983-109">すべてのテーブルでスクリプトを実行し、CDC インスタンス内のインスタンスをキャプチャするには、これを選択します。</span><span class="sxs-lookup"><span data-stu-id="19983-109">Select this to run the script on all of the tables and capture instances in the CDC instance.</span></span>  
  
 <span data-ttu-id="19983-110">これらのオプションのいずれかを選択したら、補足ログ スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="19983-110">After you select one of these options, run the supplemental logging script.</span></span>  
  
### <a name="to-run-the-supplemental-logging-scripts"></a><span data-ttu-id="19983-111">補足ログ スクリプトを実行するには</span><span class="sxs-lookup"><span data-stu-id="19983-111">To run the supplemental logging scripts</span></span>  
  
1.  <span data-ttu-id="19983-112">**[スクリプトの実行]** をクリックして、CDC インスタンスに定義されているテーブルで補足ログ スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="19983-112">Click **Run Script** to run the supplemental logging script on the tables defined for the CDC instance.</span></span> <span data-ttu-id="19983-113">このスクリプトは、キャプチャされるテーブルに UPDATE 操作のログを記録するときに、必要なすべての列をトランザクション ログに書き込むように Oracle データベースに対して指示します。</span><span class="sxs-lookup"><span data-stu-id="19983-113">This script instructs the Oracle database to write all columns of interest to its transaction logs when logging UPDATE operations to captured tables.</span></span> <span data-ttu-id="19983-114">通常、このスクリプトは Oracle システム管理者によって検査されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="19983-114">This script is normally examined and executed by an Oracle system administrator.</span></span>  
  
2.  <span data-ttu-id="19983-115">補足ログ スクリプトを実行すると、[スクリプトを実行するための Oracle 資格情報] ダイアログ ボックスが表示されます。このダイアログ ボックスで、有効な Oracle ユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="19983-115">When you run the supplemental logging scripts, the Oracle Credentials for Running Script dialog box opens where you provide a valid Oracle user name and password.</span></span> <span data-ttu-id="19983-116">適切な Oracle 資格情報を指定する方法については、「 [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19983-116">For information on how to provide the proper Oracle credentials, see [Oracle Credentials for Running Script](oracle-credentials-for-running-script.md).</span></span>  
  
 <span data-ttu-id="19983-117">必要に応じて、SQL\*Plus を使用してスクリプトを手動で実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="19983-117">You can also run the scripts manually using SQL \* Plus, if necessary.</span></span>  
  
### <a name="to-run-the-scripts-manually"></a><span data-ttu-id="19983-118">スクリプトを手動で実行するには</span><span class="sxs-lookup"><span data-stu-id="19983-118">To run the scripts manually</span></span>  
  
1.  <span data-ttu-id="19983-119">**[コピー]** をクリックしてスクリプトをクリップボードに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="19983-119">Click **Copy** to paste the script to the clipboard.</span></span> <span data-ttu-id="19983-120">SQL\*Plus を開き、Oracle ソース データベースのディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="19983-120">Open SQL\* Plus and go to the directory with your Oracle source database.</span></span> <span data-ttu-id="19983-121">SQL\*Plus にスクリプトを貼り付けて実行します。</span><span class="sxs-lookup"><span data-stu-id="19983-121">Paste the script into SQL\*Plus to run it.</span></span>  
  
### <a name="to-save-the-supplemental-logging-script-in-a-text-file"></a><span data-ttu-id="19983-122">補足ログ スクリプトをテキスト ファイルに保存するには</span><span class="sxs-lookup"><span data-stu-id="19983-122">To save the supplemental logging script in a text file</span></span>  
  
1.  <span data-ttu-id="19983-123">**[名前を付けて保存]** をクリックし、ファイルを保存する場所を参照します。</span><span class="sxs-lookup"><span data-stu-id="19983-123">Click **Save as** and browse to the location where you want to save the file.</span></span>  
  
2.  <span data-ttu-id="19983-124">ファイルに名前を付け、 **[保存]** をクリックしてファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="19983-124">Give the file a name and click **Save** to save the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19983-125">参照</span><span class="sxs-lookup"><span data-stu-id="19983-125">See Also</span></span>  
 <span data-ttu-id="19983-126">[CDC インスタンスのプロパティを編集する方法](how-to-edit-the-cdc-instance-properties.md) </span><span class="sxs-lookup"><span data-stu-id="19983-126">[How to Edit the CDC Instance Properties](how-to-edit-the-cdc-instance-properties.md) </span></span>  
 [<span data-ttu-id="19983-127">スクリプトを実行するための Oracle 資格情報</span><span class="sxs-lookup"><span data-stu-id="19983-127">Oracle Credentials for Running Script</span></span>](oracle-credentials-for-running-script.md)  
  
  
