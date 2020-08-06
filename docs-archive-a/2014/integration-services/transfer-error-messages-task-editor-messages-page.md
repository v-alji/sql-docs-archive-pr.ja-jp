---
title: '[エラーメッセージ転送タスクエディター] ([メッセージ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0d626f01e05a30777810b26880da5aedc3e7ad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646216"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a><span data-ttu-id="57412-102">[エラー メッセージ転送タスク エディター] ([メッセージ] ページ)</span><span class="sxs-lookup"><span data-stu-id="57412-102">Transfer Error Messages Task Editor (Messages Page)</span></span>
  <span data-ttu-id="57412-103">**[エラー メッセージ転送タスク エディター]** ダイアログ ボックスの **[メッセージ]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスからインスタンスへ、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー定義エラー メッセージをコピーする際のプロパティを指定できます。</span><span class="sxs-lookup"><span data-stu-id="57412-103">Use the **Messages** page of the **Transfer Error Messages Task Editor** dialog box to specify properties for copying one or more [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] user-defined error messages from one instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to another.</span></span> <span data-ttu-id="57412-104">このタスクの詳細については、「 [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57412-104">For more information about this task, see [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="57412-105">オプション</span><span class="sxs-lookup"><span data-stu-id="57412-105">Options</span></span>  
 <span data-ttu-id="57412-106">**SourceConnection**</span><span class="sxs-lookup"><span data-stu-id="57412-106">**SourceConnection**</span></span>  
 <span data-ttu-id="57412-107">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="57412-107">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the source server.</span></span>  
  
 <span data-ttu-id="57412-108">**DestinationConnection**</span><span class="sxs-lookup"><span data-stu-id="57412-108">**DestinationConnection**</span></span>  
 <span data-ttu-id="57412-109">SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="57412-109">Select a SMO connection manager in the list, or click **\<New connection...>** to create a new connection to the destination server.</span></span>  
  
 <span data-ttu-id="57412-110">**[IfObjectExists]**</span><span class="sxs-lookup"><span data-stu-id="57412-110">**IfObjectExists**</span></span>  
 <span data-ttu-id="57412-111">転送先サーバーに同じ名前のエラー メッセージが既に存在していた場合に、既存のユーザー定義エラー メッセージを上書きするか、既存のメッセージをスキップするか、タスクを失敗させるかを選択します。</span><span class="sxs-lookup"><span data-stu-id="57412-111">Select whether the task should overwrite existing user-defined error messages, skip existing messages, or fail if error messages of the same name already exist on the destination server.</span></span>  
  
 <span data-ttu-id="57412-112">**[TransferAllErrorMessages]**</span><span class="sxs-lookup"><span data-stu-id="57412-112">**TransferAllErrorMessages**</span></span>  
 <span data-ttu-id="57412-113">転送元サーバーから転送先サーバーにすべてのユーザー定義メッセージをコピーするか、指定したユーザー定義メッセージだけをコピーするかを選択します。</span><span class="sxs-lookup"><span data-stu-id="57412-113">Select whether the task should copy all or only the specified user-defined messages from the source server to the destination server.</span></span>  
  
 <span data-ttu-id="57412-114">このプロパティには、次の表に示すオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="57412-114">This property has the options listed in the following table:</span></span>  
  
|<span data-ttu-id="57412-115">値</span><span class="sxs-lookup"><span data-stu-id="57412-115">Value</span></span>|<span data-ttu-id="57412-116">説明</span><span class="sxs-lookup"><span data-stu-id="57412-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="57412-117">**True** にします</span><span class="sxs-lookup"><span data-stu-id="57412-117">**True**</span></span>|<span data-ttu-id="57412-118">すべてのユーザー定義メッセージをコピーします。</span><span class="sxs-lookup"><span data-stu-id="57412-118">Copy all user-defined messages.</span></span>|  
|<span data-ttu-id="57412-119">**False**</span><span class="sxs-lookup"><span data-stu-id="57412-119">**False**</span></span>|<span data-ttu-id="57412-120">指定されたユーザー定義メッセージのみをコピーします。</span><span class="sxs-lookup"><span data-stu-id="57412-120">Copy only the specified user-defined messages.</span></span>|  
  
 <span data-ttu-id="57412-121">**[ErrorMessagesList]**</span><span class="sxs-lookup"><span data-stu-id="57412-121">**ErrorMessagesList**</span></span>  
 <span data-ttu-id="57412-122">**[...]** ボタンをクリックして、コピーするエラー メッセージを選択します。</span><span class="sxs-lookup"><span data-stu-id="57412-122">Click the browse button **(...)** to select the error messages to copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57412-123">コピーするエラー メッセージを選択する前に **[SourceConnection]** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57412-123">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
 <span data-ttu-id="57412-124">**[ErrorMessageLanguagesList]**</span><span class="sxs-lookup"><span data-stu-id="57412-124">**ErrorMessageLanguagesList**</span></span>  
 <span data-ttu-id="57412-125">**[...]** ボタンをクリックして、転送先サーバーにコピーするユーザー定義エラー メッセージの言語を選択します。</span><span class="sxs-lookup"><span data-stu-id="57412-125">Click the browse button **(...)** to select the languages for which to copy user-defined error messages to the destination server.</span></span> <span data-ttu-id="57412-126">us_english (コード ページ 1033) バージョンのメッセージが、他言語バージョンのメッセージを転送先サーバーに転送する前に、そのサーバーに既に存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="57412-126">A us_english (code page 1033) version of the message must exist on the destination server before you can transfer other language versions of the message to that server.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57412-127">コピーするエラー メッセージを選択する前に **[SourceConnection]** を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57412-127">You must specify the **SourceConnection** before you can select error messages to copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57412-128">参照</span><span class="sxs-lookup"><span data-stu-id="57412-128">See Also</span></span>  
 <span data-ttu-id="57412-129">[Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="57412-129">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="57412-130">[Integration Services タスク](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="57412-130">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="57412-131">[[エラーメッセージ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="57412-131">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 <span data-ttu-id="57412-132">[SMO 接続マネージャー](connection-manager/smo-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="57412-132">[SMO Connection Manager](connection-manager/smo-connection-manager.md) </span></span>  
 <span data-ttu-id="57412-133">[[エラーメッセージ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="57412-133">[Transfer Error Messages Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="57412-134">SMO 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="57412-134">SMO Connection Manager</span></span>](connection-manager/smo-connection-manager.md)  
  
  
