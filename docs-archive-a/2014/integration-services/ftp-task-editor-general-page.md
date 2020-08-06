---
title: FTP タスクエディター ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0cb4ffe2fa44e76890f6b70912f84dbcaa8f2cd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633899"
---
# <a name="ftp-task-editor-general-page"></a><span data-ttu-id="9f52f-102">[FTP タスク エディター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="9f52f-102">FTP Task Editor (General Page)</span></span>
  <span data-ttu-id="9f52f-103">**[FTP タスク エディター]** ダイアログ ボックスの **[全般]** ページを使用すると、タスクの通信先の FTP サーバーに接続する FTP 接続マネージャーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9f52f-103">Use the **General** page of the **FTP Task Editor** dialog box to specify the FTP connection manager that connects to the FTP server that the task communicates with.</span></span> <span data-ttu-id="9f52f-104">また、FTP タスクの名前と説明を入力することもできます。</span><span class="sxs-lookup"><span data-stu-id="9f52f-104">You can also name and describe the FTP task.</span></span>  
  
 <span data-ttu-id="9f52f-105">このタスクの詳細については、「 [FTP タスク](control-flow/ftp-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f52f-105">To learn about this task, see [FTP Task](control-flow/ftp-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="9f52f-106">Options</span><span class="sxs-lookup"><span data-stu-id="9f52f-106">Options</span></span>  
 <span data-ttu-id="9f52f-107">**[FtpConnection]**</span><span class="sxs-lookup"><span data-stu-id="9f52f-107">**FtpConnection**</span></span>  
 <span data-ttu-id="9f52f-108">既存の FTP 接続マネージャーを選択するか、[\<**New connection...**>] をクリックして接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f52f-108">Select an existing FTP connection manager, or click \<**New connection...**> to create a connection manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9f52f-109">FTP 接続マネージャーでは、匿名認証と基本認証のみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="9f52f-109">The FTP connection manager supports only anonymous authentication and basic authentication.</span></span> <span data-ttu-id="9f52f-110">Windows 認証はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9f52f-110">It does not support Windows Authentication.</span></span>  
  
 <span data-ttu-id="9f52f-111">**関連トピック:** [FTP 接続マネージャー](connection-manager/ftp-connection-manager.md)、[FTP 接続マネージャー エディター](../../2014/integration-services/ftp-connection-manager-editor.md)</span><span class="sxs-lookup"><span data-stu-id="9f52f-111">**Related Topics**: [FTP Connection Manager](connection-manager/ftp-connection-manager.md), [FTP Connection Manager Editor](../../2014/integration-services/ftp-connection-manager-editor.md)</span></span>  
  
 <span data-ttu-id="9f52f-112">**[StopOnFailure]**</span><span class="sxs-lookup"><span data-stu-id="9f52f-112">**StopOnFailure**</span></span>  
 <span data-ttu-id="9f52f-113">FTP 操作が失敗した場合に FTP タスクを終了するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="9f52f-113">Indicate whether the FTP task terminates if an FTP operation fails.</span></span>  
  
 <span data-ttu-id="9f52f-114">**名前**</span><span class="sxs-lookup"><span data-stu-id="9f52f-114">**Name**</span></span>  
 <span data-ttu-id="9f52f-115">FTP タスクの一意な名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9f52f-115">Provide a unique name for the FTP task.</span></span> <span data-ttu-id="9f52f-116">この名前は、タスク アイコンのラベルとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f52f-116">This name is used as the label in the task icon.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9f52f-117">タスク名はパッケージ内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9f52f-117">Task names must be unique within a package.</span></span>  
  
 <span data-ttu-id="9f52f-118">**説明**</span><span class="sxs-lookup"><span data-stu-id="9f52f-118">**Description**</span></span>  
 <span data-ttu-id="9f52f-119">FTP タスクの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="9f52f-119">Type a description of the FTP task.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f52f-120">参照</span><span class="sxs-lookup"><span data-stu-id="9f52f-120">See Also</span></span>  
 <span data-ttu-id="9f52f-121">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9f52f-121">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="9f52f-122">[FTP タスクエディター &#40;ファイル転送ページ&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span><span class="sxs-lookup"><span data-stu-id="9f52f-122">[FTP Task Editor &#40;File Transfer Page&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md) </span></span>  
 <span data-ttu-id="9f52f-123">[[式] ページ](expressions/expressions-page.md)</span><span class="sxs-lookup"><span data-stu-id="9f52f-123">[Expressions Page](expressions/expressions-page.md)</span></span>  
  
  
