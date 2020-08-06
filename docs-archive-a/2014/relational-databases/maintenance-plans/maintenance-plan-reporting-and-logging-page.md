---
title: メンテナンス プラン ([レポートとログ記録] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.reportinglogging.f1
ms.assetid: 3a30b17a-3deb-446f-900a-62f88934a90f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7c7a95a7092ce2cdac4aa0540a5cb57d86b48497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639490"
---
# <a name="maintenance-plan-reporting-and-logging-page"></a><span data-ttu-id="4cd16-102">メンテナンス プラン ([レポートとログ記録] ページ)</span><span class="sxs-lookup"><span data-stu-id="4cd16-102">Maintenance Plan (Reporting and Logging Page)</span></span>
  <span data-ttu-id="4cd16-103">**[レポートとログ記録]** ダイアログ ボックスを使用して、メンテナンス プランを実行したときに生成されるレポートとログを構成できます。</span><span class="sxs-lookup"><span data-stu-id="4cd16-103">Use the **Reporting and Logging** dialog box to configure the reports and logs that are generated when maintenance plans are executed.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4cd16-104">オプション</span><span class="sxs-lookup"><span data-stu-id="4cd16-104">Options</span></span>  
 <span data-ttu-id="4cd16-105">**[テキスト ファイルのレポートを生成する]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-105">**Generate a text file report**</span></span>  
 <span data-ttu-id="4cd16-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でテキスト ファイル レポートを記述するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-106">Specify if you want [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to write a text file report.</span></span>  
  
 <span data-ttu-id="4cd16-107">**[新しいファイルの作成]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-107">**Create a new file**</span></span>  
 <span data-ttu-id="4cd16-108">メンテナンス プランの各実行に対して新しいレポート ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-108">Create a new report file for each execution of the maintenance plan.</span></span> <span data-ttu-id="4cd16-109">既定では、このメンテナンス プランが含まれている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスをホストするコンピューターにおいて、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップ中に既定のログ フォルダーとして確立されたフォルダー内にレポート ファイルが記述されます。</span><span class="sxs-lookup"><span data-stu-id="4cd16-109">By default, the report files are written to the computer hosting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that contains this maintenance plan, in the folder established as the default log folder during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="4cd16-110">別のフォルダーを指定するには、フォルダーの完全なパスを **[フォルダー]** テキスト ボックスに入力するか、参照ボタン ( **[...]** ) をクリックして目的のフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-110">To specify a different folder, enter the full path of the folder in the **Folder** text box, or click the browse button (**...**) and navigate to the desired folder.</span></span>  
  
 <span data-ttu-id="4cd16-111">**[ファイルに追加]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-111">**Append to file**</span></span>  
 <span data-ttu-id="4cd16-112">各プラン実行から、 **[ファイル名]** ボックスで指定したファイルにレポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-112">Append the report from each plan execution to the file specified in the **File name** text box.</span></span> <span data-ttu-id="4cd16-113">参照ボタンをクリックし、ダイアログ ボックスの一覧からファイルを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="4cd16-113">You may also specify a file by clicking the browse button and selecting a file from the dialog box.</span></span>  
  
 <span data-ttu-id="4cd16-114">**[電子メール受信者にレポートを送信する]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-114">**Send report to an e-mail recipient**</span></span>  
 <span data-ttu-id="4cd16-115">メンテナンス プラン実行の結果を電子メールで転送します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-115">Transmit the outcome of a maintenance plan execution via e-mail.</span></span> <span data-ttu-id="4cd16-116">このオプションは、データベース メールが有効で適切に構成されている場合にのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="4cd16-116">This option is only available if Database Mail is enabled and properly configured.</span></span>  
  
 <span data-ttu-id="4cd16-117">**[エージェント オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-117">**Agent operator**</span></span>  
 <span data-ttu-id="4cd16-118">電子メールの受信者となるエージェント オペレーターを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-118">Select an agent operator from the list who will be the recipient of the e-mail.</span></span> <span data-ttu-id="4cd16-119">このオプションは、メールが有効で適切に構成されている場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4cd16-119">This option is only available if mail is enabled and properly</span></span>  
  
 <span data-ttu-id="4cd16-120">**[拡張情報をログに記録する]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-120">**Log extended information**</span></span>  
 <span data-ttu-id="4cd16-121">追加情報をログに含めます。</span><span class="sxs-lookup"><span data-stu-id="4cd16-121">Include more information in the log.</span></span> <span data-ttu-id="4cd16-122">このオプションを指定することにより、格納されるメンテナンス プラン履歴のサイズが大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4cd16-122">Including this option will increase the size of the stored maintenance plan history.</span></span>  
  
 <span data-ttu-id="4cd16-123">**[リモート サーバーにログを記録する]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-123">**Log to remote server**</span></span>  
 <span data-ttu-id="4cd16-124">メンテナンス プランの履歴をリモート サーバーに記録します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-124">Logs maintenance plan history to a remote server.</span></span>  
  
 <span data-ttu-id="4cd16-125">**Connection**</span><span class="sxs-lookup"><span data-stu-id="4cd16-125">**Connection**</span></span>  
 <span data-ttu-id="4cd16-126">リモート サーバーにログを記録するときの接続情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-126">Specifies the connection information to use when logging to a remote server.</span></span>  
  
 <span data-ttu-id="4cd16-127">**[新規作成]**</span><span class="sxs-lookup"><span data-stu-id="4cd16-127">**New**</span></span>  
 <span data-ttu-id="4cd16-128">**[接続プロパティ]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-128">Displays the **Connection Properties** dialog box.</span></span> <span data-ttu-id="4cd16-129">リモート サーバーにログを記録するための新しい接続情報を構成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="4cd16-129">Used to configure new connection information for logging to a remote server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cd16-130">参照</span><span class="sxs-lookup"><span data-stu-id="4cd16-130">See Also</span></span>  
 <span data-ttu-id="4cd16-131">[メンテナンス プラン](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="4cd16-131">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="4cd16-132">データベース メール</span><span class="sxs-lookup"><span data-stu-id="4cd16-132">Database Mail</span></span>](../database-mail/database-mail.md)  
  
  
