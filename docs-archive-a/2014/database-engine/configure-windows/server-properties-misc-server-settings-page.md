---
title: サーバーのプロパティ ([その他のサーバーの設定] ページ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.miscserversettings.f1
ms.assetid: b170c066-30cd-42dd-8d34-aa129ea09551
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9a82a787140141c3bfa7b18776328a813be9f41f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641858"
---
# <a name="server-properties-misc-server-settings-page"></a><span data-ttu-id="97474-102">[サーバーのプロパティ] ([その他のサーバーの設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="97474-102">Server Properties (Misc Server Settings Page)</span></span>
  <span data-ttu-id="97474-103">このページを使用すると、サーバーの設定を表示したり、変更したりできます。</span><span class="sxs-lookup"><span data-stu-id="97474-103">Use this page to view or modify your server settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="97474-104">Options</span><span class="sxs-lookup"><span data-stu-id="97474-104">Options</span></span>  
 <span data-ttu-id="97474-105">**[ユーザーの既定の言語]**</span><span class="sxs-lookup"><span data-stu-id="97474-105">**Default language for users**</span></span>  
 <span data-ttu-id="97474-106">新しく作成するすべてのログインの既定の言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="97474-106">Specifies the default language for all newly created logins.</span></span>  
  
 <span data-ttu-id="97474-107">**[トリガーによる他のトリガーの起動を許可する]**</span><span class="sxs-lookup"><span data-stu-id="97474-107">**Allow triggers to fire other triggers**</span></span>  
 <span data-ttu-id="97474-108">トリガーによって別のトリガーを起動するアクションを実行するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="97474-108">Controls whether a trigger can perform an action that initiates another trigger.</span></span> <span data-ttu-id="97474-109">このオプションをオフにすると、トリガーは別のトリガーによって起動されません。</span><span class="sxs-lookup"><span data-stu-id="97474-109">When cleared, triggers cannot be fired by another trigger.</span></span> <span data-ttu-id="97474-110">このオプションをオンにすると、トリガーは最大 32 レベルまで別のトリガーによって起動されます。</span><span class="sxs-lookup"><span data-stu-id="97474-110">When selected, triggers can be fired by other triggers to as many as 32 levels.</span></span>  
  
 <span data-ttu-id="97474-111">**[クエリの実行時間が長くならないようにクエリ ガバナーを使用する]**</span><span class="sxs-lookup"><span data-stu-id="97474-111">**Use query governor to prevent long-running queries**</span></span>  
 <span data-ttu-id="97474-112">クエリを実行する最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="97474-112">Specifies an upper limit on the time within which a query can run.</span></span> <span data-ttu-id="97474-113">クエリ コストとは、特定のハードウェア構成でクエリを実行するために必要とされる予測所要時間を秒単位で表したものです。</span><span class="sxs-lookup"><span data-stu-id="97474-113">Query cost refers to the estimated elapsed time, in seconds, required to execute a query on a specific hardware configuration.</span></span> <span data-ttu-id="97474-114">既定では、クエリ カバナはオフになっており、すべてのクエリは実行が許可されています。</span><span class="sxs-lookup"><span data-stu-id="97474-114">By default, the query governor is turned off and all queries are allowed to run.</span></span> <span data-ttu-id="97474-115">このオプションをオンにする場合は、下のテキスト ボックスに時間制限を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97474-115">If this option is selected, you must enter a time limit in the text box below.</span></span> <span data-ttu-id="97474-116">0 以外の正の値を指定すると、クエリ ガバナーは、見積コストがこの値を超えるクエリの実行を許可しません。</span><span class="sxs-lookup"><span data-stu-id="97474-116">If you specify a nonzero, nonnegative value, the query governor disallows execution of any query that has an estimated cost exceeding that value.</span></span>  
  
 <span data-ttu-id="97474-117">**[2 桁の年を以下の間にある年として解釈]**</span><span class="sxs-lookup"><span data-stu-id="97474-117">**Interpret a two-digit year as falling between**</span></span>  
 <span data-ttu-id="97474-118">2 桁の年の値を解釈するために 100 年の日付範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="97474-118">Specifies the 100-year date range for interpreting two-digit year values.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="97474-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、2 桁の日付値を解釈するときに、その 2 桁で終わる年を、指定された範囲の中から参照します。</span><span class="sxs-lookup"><span data-stu-id="97474-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will interpret two-digit date values to refer to the year ending in those digits that falls within the specified range.</span></span>  
  
 <span data-ttu-id="97474-120">右のボックスで終了年を設定します。</span><span class="sxs-lookup"><span data-stu-id="97474-120">Set the right box with the ending year.</span></span> <span data-ttu-id="97474-121">終了年が保存されると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の左のボックスに自動的に開始年が入力されます。</span><span class="sxs-lookup"><span data-stu-id="97474-121">When the ending year is saved, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will automatically populate the left box with the beginning year.</span></span>  
  
 <span data-ttu-id="97474-122">**[構成した値]**</span><span class="sxs-lookup"><span data-stu-id="97474-122">**Configured Values**</span></span>  
 <span data-ttu-id="97474-123">このペインの各オプションに構成されている値を表示します。</span><span class="sxs-lookup"><span data-stu-id="97474-123">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="97474-124">これらの値を変更した場合は、 **[実行中の値]** をクリックして、変更後の値が反映されているかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="97474-124">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="97474-125">値が反映されていない場合は、先に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを再指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97474-125">If the changes have not taken effect, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="97474-126">**[実行中の値]**</span><span class="sxs-lookup"><span data-stu-id="97474-126">**Running Values**</span></span>  
 <span data-ttu-id="97474-127">このペイン上のオプションの、現在実行中の値を表示します。</span><span class="sxs-lookup"><span data-stu-id="97474-127">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="97474-128">これらの値は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="97474-128">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97474-129">参照</span><span class="sxs-lookup"><span data-stu-id="97474-129">See Also</span></span>  
 [<span data-ttu-id="97474-130">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="97474-130">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
