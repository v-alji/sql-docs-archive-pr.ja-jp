---
title: '[警告のプロパティ]-[新しい警告] ([応答] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 34e7f11ff3210ec4fc1835751bc35b140d3fa0ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737489"
---
# <a name="alert-properties-new-alert-response-page"></a><span data-ttu-id="717a4-102">[警告のプロパティ]-[新しい警告] ([応答] ページ)</span><span class="sxs-lookup"><span data-stu-id="717a4-102">Alert Properties-New Alert (Response Page)</span></span>
  <span data-ttu-id="717a4-103">このページを使用すると、実行するジョブを指定したり、エージェントの警告に応答して通知を受けるオペレーターの一覧を取得したりでき [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="717a4-103">Use this page to specify a job that you want to run and to obtain a list of operators to be notified in response to a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alert.</span></span>  
  
## <a name="options"></a><span data-ttu-id="717a4-104">Options</span><span class="sxs-lookup"><span data-stu-id="717a4-104">Options</span></span>  
 <span data-ttu-id="717a4-105">**[ジョブの実行]**</span><span class="sxs-lookup"><span data-stu-id="717a4-105">**Execute job**</span></span>  
 <span data-ttu-id="717a4-106">**[ジョブ一覧]**、 **[新しいジョブ]** 、および **[ジョブの表示]** の各オプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="717a4-106">Enables the **Job list**, **New job** and **View job** options.</span></span>  
  
 <span data-ttu-id="717a4-107">**新しいジョブ**</span><span class="sxs-lookup"><span data-stu-id="717a4-107">**New job**</span></span>  
 <span data-ttu-id="717a4-108">**[新しいジョブ]** ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="717a4-108">Open the **New Job** dialog box.</span></span> <span data-ttu-id="717a4-109">**[ジョブの実行]** が選択されていない場合、このボタンは使用できません。</span><span class="sxs-lookup"><span data-stu-id="717a4-109">This button is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="717a4-110">**ジョブの表示**</span><span class="sxs-lookup"><span data-stu-id="717a4-110">**View job**</span></span>  
 <span data-ttu-id="717a4-111">選択されているジョブを表示または変更します。</span><span class="sxs-lookup"><span data-stu-id="717a4-111">View or modify the selected job.</span></span> <span data-ttu-id="717a4-112">**[ジョブの実行]** が選択されていない場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="717a4-112">This option is not available when **Execute job** is not selected.</span></span>  
  
 <span data-ttu-id="717a4-113">**[オペレーターに通知する]**</span><span class="sxs-lookup"><span data-stu-id="717a4-113">**Notify operators**</span></span>  
 <span data-ttu-id="717a4-114">オペレーターを追加、削除、または変更できるようにするためのコントロールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="717a4-114">Enables the controls that allow you to add, remove, or change operators.</span></span>  
  
 <span data-ttu-id="717a4-115">**[オペレーター一覧]**</span><span class="sxs-lookup"><span data-stu-id="717a4-115">**Operator list**</span></span>  
 <span data-ttu-id="717a4-116">警告の発生時に通知するオペレーターの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="717a4-116">Lists the operators to notify when an alert occurs.</span></span> <span data-ttu-id="717a4-117">通知方法を指定するには、オペレーター名の後に表示されている **[電子メール]**、 **[ポケットベル]**、または **[Net Send]** チェック ボックスをオンにします。 **[オペレーターに通知する]** が選択されていない場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="717a4-117">To specify a notification method, select the **E-mail**, **Pager**, or **Net send** check box that is displayed after the operator name.This option not available when **Notify operators** is not selected.</span></span>  
  
 <span data-ttu-id="717a4-118">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="717a4-118">**E-mail**</span></span>  
 <span data-ttu-id="717a4-119">電子メールを使用してオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="717a4-119">Use e-mail to notify the operator.</span></span>  
  
 <span data-ttu-id="717a4-120">**ポケットベル**</span><span class="sxs-lookup"><span data-stu-id="717a4-120">**Pager**</span></span>  
 <span data-ttu-id="717a4-121">ポケットベルの電子メール アドレスを使用してオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="717a4-121">Use the pager e-mail address to notify the operator.</span></span>  
  
 <span data-ttu-id="717a4-122">**Net send**</span><span class="sxs-lookup"><span data-stu-id="717a4-122">**Net send**</span></span>  
 <span data-ttu-id="717a4-123">**net send** を使用してオペレーターに通知します。</span><span class="sxs-lookup"><span data-stu-id="717a4-123">Use **net send** to notify the operator.</span></span>  
  
 <span data-ttu-id="717a4-124">**[新しいオペレーター]**</span><span class="sxs-lookup"><span data-stu-id="717a4-124">**New operator**</span></span>  
 <span data-ttu-id="717a4-125">**[新しいオペレーター]** ダイアログ ボックスを表示します。このダイアログ ボックスを使用して、新しいオペレーターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="717a4-125">Displays the **New Operator** dialog box, which you can use to create a new operator.</span></span>  
  
 <span data-ttu-id="717a4-126">**[オペレーターの表示]**</span><span class="sxs-lookup"><span data-stu-id="717a4-126">**View operator**</span></span>  
 <span data-ttu-id="717a4-127">現在選択されているオペレーターの **[プロパティ]** ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="717a4-127">Displays the **Properties** dialog box for the currently selected operator.</span></span> <span data-ttu-id="717a4-128">**[オペレーターのプロパティ]** ダイアログ ボックスで、オペレーターのプロパティを表示および変更できます。</span><span class="sxs-lookup"><span data-stu-id="717a4-128">You can view and modified operator properties on the **Operator Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717a4-129">参照</span><span class="sxs-lookup"><span data-stu-id="717a4-129">See Also</span></span>  
 <span data-ttu-id="717a4-130">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="717a4-130">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="717a4-131">[重大度レベルを使用してアラートを作成する](create-an-alert-using-severity-level.md) </span><span class="sxs-lookup"><span data-stu-id="717a4-131">[Create an Alert Using Severity Level](create-an-alert-using-severity-level.md) </span></span>  
 <span data-ttu-id="717a4-132">[Alerts](alerts.md) </span><span class="sxs-lookup"><span data-stu-id="717a4-132">[Alerts](alerts.md) </span></span>  
 <span data-ttu-id="717a4-133">[アラートを編集する](edit-an-alert.md) </span><span class="sxs-lookup"><span data-stu-id="717a4-133">[Edit an Alert](edit-an-alert.md) </span></span>  
 [<span data-ttu-id="717a4-134">Delete an Alert</span><span class="sxs-lookup"><span data-stu-id="717a4-134">Delete an Alert</span></span>](delete-an-alert.md)  
  
  
