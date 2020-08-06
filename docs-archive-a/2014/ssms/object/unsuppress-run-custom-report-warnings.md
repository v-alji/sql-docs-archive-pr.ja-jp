---
title: カスタム レポート実行時の警告の抑制を解除する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
ms.openlocfilehash: 725362ff7f8a6c282529f652e8813a8083257eb8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711537"
---
# <a name="unsuppress-run-custom-report-warnings"></a><span data-ttu-id="a515e-102">カスタム レポート実行時の警告の抑制を解除する方法</span><span class="sxs-lookup"><span data-stu-id="a515e-102">Unsuppress Run Custom Report Warnings</span></span>
  <span data-ttu-id="a515e-103">カスタム レポートについて表示される警告ダイアログ ボックスは 2 種類あります。</span><span class="sxs-lookup"><span data-stu-id="a515e-103">There are two warning dialog boxes for custom reports.</span></span> <span data-ttu-id="a515e-104">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、これらのボックスの表示抑制を解除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a515e-104">This topic describes how to unsuppress the display of these boxes in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="a515e-105">既定で、 **[カスタム レポートの実行]** ダイアログ ボックスはカスタム レポートが実行される前に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a515e-105">By default, the **Run Custom Reports** dialog box appears before a custom report runs.</span></span> <span data-ttu-id="a515e-106">**[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a515e-106">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span> <span data-ttu-id="a515e-107">また、カスタム レポートを開き、リンクをクリックして別のカスタム レポートを開いたときにも、既定で **[カスタム レポートの実行]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a515e-107">Also by default, the **Run Custom Reports** dialog box appears when you open a custom report and then click a link to open another custom report.</span></span> <span data-ttu-id="a515e-108">このダイアログ ボックスにはドリルスルー カスタム レポート ファイルへの完全パスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a515e-108">This dialog box displays the fill path to the drill-through custom report file.</span></span> <span data-ttu-id="a515e-109">**[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a515e-109">If you select the **Please don't show this warning again** check box, the dialog box will no longer appear.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a515e-110">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="a515e-110">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a><span data-ttu-id="a515e-111">メインのカスタム レポート警告ダイアログ ボックスの抑制を解除するには</span><span class="sxs-lookup"><span data-stu-id="a515e-111">To unsuppress the main custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="a515e-112">\<*Server*> \\ < *共有* >| \<*Drive*> \Documents と設定 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml に接続します。</span><span class="sxs-lookup"><span data-stu-id="a515e-112">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="a515e-113">を右クリック `reports.xml` し、[**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a515e-113">Right-click `reports.xml`, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="a515e-114">\*\* \<SuppressWarning> True \</SuppressWarning> を \<SuppressWarning> false \</SuppressWarning> に\*\*変更します。</span><span class="sxs-lookup"><span data-stu-id="a515e-114">Change**\<SuppressWarning>true\</SuppressWarning> to \<SuppressWarning>false\</SuppressWarning>**.</span></span>  
  
4.  <span data-ttu-id="a515e-115">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="a515e-115">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a><span data-ttu-id="a515e-116">ドリルスルー カスタム レポート警告ダイアログ ボックスの抑制を解除するには</span><span class="sxs-lookup"><span data-stu-id="a515e-116">To unsuppress the drill-through custom report warning dialog box</span></span>  
  
1.  <span data-ttu-id="a515e-117">\<*Server*> \\ < *共有* >| \<*Drive*> \Documents と設定 \\<UserProfile \> \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml に接続します。</span><span class="sxs-lookup"><span data-stu-id="a515e-117">Connect to \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.</span></span>  
  
2.  <span data-ttu-id="a515e-118">を右クリック `reports.xml` し、[**編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a515e-118">Right-click `reports.xml`, and click **Edit**.</span></span>  
  
3.  <span data-ttu-id="a515e-119">\*\* \<SuppressDrillthroughWarning> True \</SuppressDrillthroughWarning> を \<SuppressDrillthroughWarning> false \</SuppressDrillthroughWarning> に\*\*変更します。</span><span class="sxs-lookup"><span data-stu-id="a515e-119">Change **\<SuppressDrillthroughWarning>true\</SuppressDrillthroughWarning>to \<SuppressDrillthroughWarning>false\</SuppressDrillthroughWarning>**.</span></span>  
  
4.  <span data-ttu-id="a515e-120">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を再起動します。</span><span class="sxs-lookup"><span data-stu-id="a515e-120">Restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a515e-121">参照</span><span class="sxs-lookup"><span data-stu-id="a515e-121">See Also</span></span>  
 <span data-ttu-id="a515e-122">[Management Studio のカスタムレポート](custom-reports-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a515e-122">[Custom Reports in Management Studio](custom-reports-in-management-studio.md) </span></span>  
 <span data-ttu-id="a515e-123">[カスタムレポートを Management Studio に追加する](add-a-custom-report-to-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="a515e-123">[Add a Custom Report to Management Studio](add-a-custom-report-to-management-studio.md) </span></span>  
 [<span data-ttu-id="a515e-124">カスタム レポートでのオブジェクト エクスプローラー ノード プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="a515e-124">Use Custom Reports with Object Explorer Node Properties</span></span>](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
