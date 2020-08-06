---
title: プロキシを使用するマルチサーバー ジョブのトラブルシューティング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], multiserver jobs
- jobs [SQL Server Agent], multiserver jobs using proxies
ms.assetid: fc579bd3-010c-4f72-8b5c-d0cc18a1f280
author: stevestein
ms.author: sstein
ms.openlocfilehash: 19de975ef5e1f22c93cec72a5014a01da5b03dd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714986"
---
# <a name="troubleshoot-multiserver-jobs-that-use-proxies"></a><span data-ttu-id="1f416-102">プロキシを使用するマルチサーバー ジョブのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1f416-102">Troubleshoot Multiserver Jobs That Use Proxies</span></span>
  <span data-ttu-id="1f416-103">プロキシに関連付けられているステップがある分散ジョブは、ターゲット サーバーのプロキシ アカウントのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1f416-103">Distributed jobs whose steps are associated with a proxy run under the context of the proxy account on the target server.</span></span> <span data-ttu-id="1f416-104">プロキシ アカウントを使用するジョブ ステップをマスター サーバーからダウンロードする際、それらのジョブ ステップにエラーが発生した場合は、 **msdb** データベースの **sysdownloadlist** テーブルにある **error_message** 列に次のエラー メッセージが出力されていないか確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f416-104">If job steps that use proxy accounts fail when downloaded from the master server, check the **error_message** column in the **sysdownloadlist** table in the **msdb** database for the following error messages:</span></span>  
  
-   <span data-ttu-id="1f416-105">"ジョブ ステップではプロキシ アカウントが必要ですが、ターゲット サーバーで一致するプロキシが無効です。"</span><span class="sxs-lookup"><span data-stu-id="1f416-105">"The job step requires a proxy account, however proxy matching is disabled on the target server."</span></span>  
  
     <span data-ttu-id="1f416-106">このエラーを解決するには、 **\ HKEY_LOCAL_MACHINE \SOFTWARE\MICROSOFT\MICROSOFT SQL Server\MSSQL.** を設定します。_ \<n_> **\SQLServerAgent\AllowDownloadedJobsToMatchProxyName**レジストリサブキーを**1 (true)** にします。</span><span class="sxs-lookup"><span data-stu-id="1f416-106">To resolve this error, set the **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL.**_\<n_>**\SQLServerAgent\AllowDownloadedJobsToMatchProxyName** registry subkey to **1 (true)**.</span></span> <span data-ttu-id="1f416-107">既定では、このサブキーは**0** () に設定されて `false` います。</span><span class="sxs-lookup"><span data-stu-id="1f416-107">By default, this subkey is set to **0** (`false`).</span></span> <span data-ttu-id="1f416-108">MSSQL の値 **。**\<*n*></span><span class="sxs-lookup"><span data-stu-id="1f416-108">The value of **MSSQL.**\<*n*></span></span> <span data-ttu-id="1f416-109">インスタンス名を指定します。たとえば、 **mssql. 1**または**mssql. 3**のようになります。</span><span class="sxs-lookup"><span data-stu-id="1f416-109">is the instance name; for example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
-   <span data-ttu-id="1f416-110">"プロキシ アカウントが見つかりませんでした。"</span><span class="sxs-lookup"><span data-stu-id="1f416-110">"Proxy not found."</span></span>  
  
     <span data-ttu-id="1f416-111">このエラーを解決するには、ターゲット サーバー上にプロキシ アカウントが存在し、ジョブ ステップを実行するマスター サーバー プロキシ アカウントと同じ名前が付けられているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f416-111">To resolve this error, make sure a proxy account exists on the target server with the same name as the master server proxy account under which the job step runs.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f416-112">参照</span><span class="sxs-lookup"><span data-stu-id="1f416-112">See Also</span></span>  
 [<span data-ttu-id="1f416-113">マルチサーバー環境の作成</span><span class="sxs-lookup"><span data-stu-id="1f416-113">Create a Multiserver Environment</span></span>](create-a-multiserver-environment.md)  
  
  
