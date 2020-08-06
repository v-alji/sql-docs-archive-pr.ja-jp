---
title: トレース データへのアクセスを向上させる | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], space
- SQL Server Profiler, space
- space [SQL Server], SQL Server Profiler
ms.assetid: c260c000-fd53-4831-993f-df6894f3228b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60e01ad04ddd9f7fe6d858c399abb552716f2bea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713974"
---
# <a name="improve-access-to-trace-data"></a><span data-ttu-id="b1b72-102">トレース データへのアクセスを向上させる</span><span class="sxs-lookup"><span data-stu-id="b1b72-102">Improve Access to Trace Data</span></span>
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="b1b72-103">は、トレース データのアクセスを向上させるために、 **temp** ディレクトリの領域を使用します。</span><span class="sxs-lookup"><span data-stu-id="b1b72-103">uses space in the **temp** directory to improve access to trace data.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="b1b72-104">には、最低で 10 MB の空き領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="b1b72-104">requires at least 10 megabytes (MB) of free space.</span></span> <span data-ttu-id="b1b72-105">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]の使用中に空き容量が 10 MB より少なくなると、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] のすべての機能が停止します。</span><span class="sxs-lookup"><span data-stu-id="b1b72-105">If free space drops below 10 MB while you are using [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], all [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] functions stop.</span></span>  
  
 <span data-ttu-id="b1b72-106">[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によって **temp** ディレクトリの領域が使用されると、 **temp** ディレクトリのサイズがすぐに大きくなってしまう場合があります。</span><span class="sxs-lookup"><span data-stu-id="b1b72-106">When [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] uses space in the **temp** directory, this space usage may cause the **temp** directory to grow rapidly.</span></span> <span data-ttu-id="b1b72-107">ファイル サイズ増大の問題を防ぐために、TEMP 環境変数の値を変更して、 **temp** ディレクトリをシステム ドライブでないドライブに配置することができます。</span><span class="sxs-lookup"><span data-stu-id="b1b72-107">To avoid file-growth problems, you can place the **temp** directory on a drive that is not a system drive by changing the value for the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="b1b72-108">以下の手順は、ほとんどの Microsoft Windows オペレーティング システムで TEMP 環境変数の値を変更する方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="b1b72-108">The following procedure describes how to change the value for the TEMP environment variable in most Microsoft Windows operating systems.</span></span> <span data-ttu-id="b1b72-109">環境変数の設定の詳細については、お使いの Windows オペレーティング システムのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1b72-109">For more information about setting environment variables, see your Windows operating system documentation.</span></span>  
  
### <a name="to-change-the-temp-environment-variable-in-windows-operating-systems"></a><span data-ttu-id="b1b72-110">Windows オペレーティング システムで TEMP 環境変数を変更するには</span><span class="sxs-lookup"><span data-stu-id="b1b72-110">To change the TEMP environment variable in Windows operating systems</span></span>  
  
1.  <span data-ttu-id="b1b72-111">**[スタート]** メニューの **[コントロール パネル]** をクリックし、 **[システム]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1b72-111">On the **Start** menu, choose **Control Panel**, and then click **System**.</span></span>  
  
2.  <span data-ttu-id="b1b72-112">**[システムのプロパティ]** ダイアログ ボックスで、 **[詳細設定]** タブをクリックし、 **[環境変数]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1b72-112">In the **System Properties** dialog box, click the **Advanced** tab, and then click **Environment Variables**.</span></span>  
  
3.  <span data-ttu-id="b1b72-113">**[システム環境変数]** ボックスの一覧をスクロールして、 **TEMP** 変数の行をクリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1b72-113">Scroll down the list of **System Variables**, select the row that corresponds to the **TEMP** variable, and click **Edit**.</span></span>  
  
4.  <span data-ttu-id="b1b72-114">**[システム変数の編集]** ダイアログ ボックスで、 **temp** ディレクトリを配置するドライブとディレクトリのパスと名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b1b72-114">In the **Edit System Variable** dialog box, enter the path and name of the drive and directory where you want the **temp** directory to be located.</span></span>  
  
5.  <span data-ttu-id="b1b72-115">**[OK]** をクリックして変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="b1b72-115">Click **OK** to save the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b72-116">参照</span><span class="sxs-lookup"><span data-stu-id="b1b72-116">See Also</span></span>  
 <span data-ttu-id="b1b72-117">[SQL Server Profiler の起動](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="b1b72-117">[Start SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="b1b72-118">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="b1b72-118">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
