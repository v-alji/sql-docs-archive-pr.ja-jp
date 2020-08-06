---
title: '[演算子のプロパティ] と [新しい演算子] ([全般] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.operator.general.f1
ms.assetid: c036d1c9-83d1-4a95-b67e-29d283b1a046
author: stevestein
ms.author: sstein
ms.openlocfilehash: 11ffd4a604275153a2bfe7071c442cc110815f81
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634787"
---
# <a name="operator-properties-and-new-operator-general-page"></a><span data-ttu-id="bbfb1-102">[オペレーターのプロパティ] および [新しいオペレーター] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="bbfb1-102">Operator Properties and New Operator (General Page)</span></span>
  <span data-ttu-id="bbfb1-103">このページを使用すると、エージェントオペレーターの全般プロパティを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-103">Use this page to view and modify the general properties of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operators.</span></span>  
  
## <a name="options"></a><span data-ttu-id="bbfb1-104">Options</span><span class="sxs-lookup"><span data-stu-id="bbfb1-104">Options</span></span>  
 <span data-ttu-id="bbfb1-105">**名前**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-105">**Name**</span></span>  
 <span data-ttu-id="bbfb1-106">オペレーターの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-106">Change the name of the operator.</span></span>  
  
 <span data-ttu-id="bbfb1-107">**有効**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-107">**Enabled**</span></span>  
 <span data-ttu-id="bbfb1-108">オペレーターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-108">Enable the operator.</span></span> <span data-ttu-id="bbfb1-109">有効になっていない場合は、オペレーターに通知が送信されません。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-109">When not enabled, no notifications are sent to the operator.</span></span>  
  
 <span data-ttu-id="bbfb1-110">**[電子メール名]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-110">**E-mail name**</span></span>  
 <span data-ttu-id="bbfb1-111">オペレーターの電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-111">Specifies the e-mail address for the operator.</span></span>  
  
 <span data-ttu-id="bbfb1-112">**[Net Send アドレス]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-112">**Net send address**</span></span>  
 <span data-ttu-id="bbfb1-113">**net send**に使用するアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-113">Specify the address to use for **net send**.</span></span>  
  
 <span data-ttu-id="bbfb1-114">**[ポケットベル用電子メール ログイン名]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-114">**Pager e-mail name**</span></span>  
 <span data-ttu-id="bbfb1-115">オペレーターのポケットベルに使用する電子メール アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-115">Specifies the e-mail address to use for the operator's pager.</span></span>  
  
 <span data-ttu-id="bbfb1-116">**[ポケットベルの受信スケジュール]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-116">**Pager on duty schedule**</span></span>  
 <span data-ttu-id="bbfb1-117">ポケットベルをアクティブにする時間を設定します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-117">Sets the times at which the pager is active.</span></span>  
  
 <span data-ttu-id="bbfb1-118">**[月曜日] ～ [日曜日]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-118">**Monday - Sunday**</span></span>  
 <span data-ttu-id="bbfb1-119">ポケットベルをアクティブにする日を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-119">Select the days that the pager is active.</span></span>  
  
 <span data-ttu-id="bbfb1-120">**[始業時刻]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-120">**Workday begin**</span></span>  
 <span data-ttu-id="bbfb1-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがポケットベルへのメッセージ送信を開始する時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-121">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent sends messages to the pager.</span></span>  
  
 <span data-ttu-id="bbfb1-122">**[終業時刻]**</span><span class="sxs-lookup"><span data-stu-id="bbfb1-122">**Workday end**</span></span>  
 <span data-ttu-id="bbfb1-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがポケットベルへのメッセージ送信を終了する時刻を選択します。</span><span class="sxs-lookup"><span data-stu-id="bbfb1-123">Select the time of day after which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent no longer sends messages to the pager.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfb1-124">参照</span><span class="sxs-lookup"><span data-stu-id="bbfb1-124">See Also</span></span>  
 [<span data-ttu-id="bbfb1-125">オペレーター</span><span class="sxs-lookup"><span data-stu-id="bbfb1-125">Operators</span></span>](operators.md)  
  
  
