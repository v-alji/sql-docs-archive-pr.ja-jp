---
title: HOST_NAME 値 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.hostnamevalue.f1
ms.assetid: 21548f08-2910-4a55-baac-b911ba9afaf1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 67d01df05c8d56fd435eb0ee1b42ba2da6a312ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632342"
---
# <a name="host_name-values"></a><span data-ttu-id="f0ed0-102">[HOST_NAME 値]</span><span class="sxs-lookup"><span data-stu-id="f0ed0-102">HOST_NAME Values</span></span>
  <span data-ttu-id="f0ed0-103">パラメーター化されたフィルター付きのマージ パブリケーションは、SUSER_SNAME() 関数または HOST_NAME() 関数を使用してデータにフィルターをかけます。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-103">Merge publications with parameterized filters use the SUSER_SNAME() function and/or the HOST_NAME() function to filter data.</span></span> <span data-ttu-id="f0ed0-104">関数は、パブリケーションの新規作成ウィザードまたは **[パブリケーションのプロパティ]** ダイアログ ボックスで指定します。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-104">The function is specified in the New Publication Wizard or the **Publication Properties** dialog box.</span></span>  
  
 <span data-ttu-id="f0ed0-105">既定では、HOST_NAME() 関数は、パブリッシャーに接続しているコンピューターの名前を返します。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-105">By default, the HOST_NAME() function returns the name of the computer connecting to the Publisher.</span></span> <span data-ttu-id="f0ed0-106">通常、パラメーター化されたフィルターを使用する場合は、ウィザードのこのページで値を指定してこの値をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-106">When using parameterized filters, it is common to override this value by supplying a value on this page of the wizard.</span></span> <span data-ttu-id="f0ed0-107">これにより、HOST_NAME() 関数は、コンピューターの名前ではなく、指定された値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-107">The HOST_NAME() function then returns the value you specify rather than the name of the computer.</span></span> <span data-ttu-id="f0ed0-108">詳細については、「[Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)」 (パラメーター化された行フィルター) の "Overriding the HOST_NAME() Value" (HOST_NAME() 値のオーバーライド) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-108">For more information, see the "Overriding the HOST_NAME() Value" section of [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0ed0-109">HOST_NAME() をオーバーライドした場合、HOST_NAME() 関数のすべての呼び出しは、指定された値を返します。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-109">If you override HOST_NAME(), all calls to the HOST_NAME() function will return the value you specify.</span></span> <span data-ttu-id="f0ed0-110">他のアプリケーションが、コンピューター名を返す HOST_NAME() 関数に依存していないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-110">Ensure that other applications are not depending on HOST_NAME() returning the computer name.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f0ed0-111">オプション</span><span class="sxs-lookup"><span data-stu-id="f0ed0-111">Options</span></span>  
 <span data-ttu-id="f0ed0-112">**[サブスクリプションのプロパティ]**</span><span class="sxs-lookup"><span data-stu-id="f0ed0-112">**Subscription properties**</span></span>  
 <span data-ttu-id="f0ed0-113">サブスクライバーごとに **[HOST_NAME 値]** 列に値を入力するか、既定値を受け入れます。既定値は、サブスクライバー コンピューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="f0ed0-113">Enter a value for each Subscriber in the **HOST_NAME Value** column or accept the default, which is the name of the Subscriber computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ed0-114">参照</span><span class="sxs-lookup"><span data-stu-id="f0ed0-114">See Also</span></span>  
 <span data-ttu-id="f0ed0-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed0-115">[Create a Pull Subscription](create-a-pull-subscription.md) </span></span>  
 <span data-ttu-id="f0ed0-116">[ssSDSFull](create-a-push-subscription.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed0-116">[Create a Push Subscription](create-a-push-subscription.md) </span></span>  
 <span data-ttu-id="f0ed0-117">[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed0-117">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="f0ed0-118">[プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f0ed0-118">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="f0ed0-119">[HOST_NAME (Transact-SQL)](/sql/t-sql/functions/host-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f0ed0-119">[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql) </span></span>  
 [<span data-ttu-id="f0ed0-120">パブリケーションのサブスクライブ</span><span class="sxs-lookup"><span data-stu-id="f0ed0-120">Subscribe to Publications</span></span>](subscribe-to-publications.md)  
  
  
