---
title: '[サーバーへの接続] (Oracle)、[接続プロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4c76a3058283a098357701a44de48efff917acd7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631833"
---
# <a name="connect-to-server-oracle-connection-properties"></a><span data-ttu-id="00f3b-102">[サーバーへの接続] (Oracle)、[接続プロパティ]</span><span class="sxs-lookup"><span data-stu-id="00f3b-102">Connect to Server (Oracle), Connection Properties</span></span>
  <span data-ttu-id="00f3b-103">**[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブを使用すると、 **[ゲートウェイ]** または **[完全]** のパブリッシュ オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="00f3b-103">Use the **Connection Properties** tab of the **Connect to Server** dialog box to specify a publishing option of **Gateway** or **Complete**.</span></span> <span data-ttu-id="00f3b-104">パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。</span><span class="sxs-lookup"><span data-stu-id="00f3b-104">After a Publisher is identified, this option cannot be changed without dropping and reconfiguring the Publisher.</span></span> <span data-ttu-id="00f3b-105">詳細については、「[Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="00f3b-105">For more information, see [Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="00f3b-106">オプション</span><span class="sxs-lookup"><span data-stu-id="00f3b-106">Options</span></span>  
 <span data-ttu-id="00f3b-107">**パブリッシャーの種類**</span><span class="sxs-lookup"><span data-stu-id="00f3b-107">**Publisher type**</span></span>  
 <span data-ttu-id="00f3b-108">**[ゲートウェイ]** または **[完全]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="00f3b-108">Select **Gateway** or **Complete**.</span></span> <span data-ttu-id="00f3b-109">**[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。</span><span class="sxs-lookup"><span data-stu-id="00f3b-109">The **Complete** option is designed to provide snapshot and transactional publications with the complete set of supported features for Oracle publishing.</span></span> <span data-ttu-id="00f3b-110">**[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="00f3b-110">The **Gateway** option provides specific design optimizations to improve performance for cases where replication serves as a gateway between systems.</span></span> <span data-ttu-id="00f3b-111">複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="00f3b-111">The **Gateway** option cannot be used if you plan to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="00f3b-112">**[ゲートウェイ]** オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="00f3b-112">A table can appear in at most one transactional publication and any number of snapshot publications if you select **Gateway**.</span></span>  
  
 <span data-ttu-id="00f3b-113">**[タイムアウト]**</span><span class="sxs-lookup"><span data-stu-id="00f3b-113">**Timeouts**</span></span>  
 <span data-ttu-id="00f3b-114">タイムアウト エラーが発生する前に [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターが Oracle パブリッシャーへの接続を試みる期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="00f3b-114">Specify how long the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributor should attempt to connect to the Oracle Publisher before a timeout error occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f3b-115">参照</span><span class="sxs-lookup"><span data-stu-id="00f3b-115">See Also</span></span>  
 <span data-ttu-id="00f3b-116">[Glossary of Terms for Oracle Publishing (Oracle パブリッシングの用語)](non-sql/glossary-of-terms-for-oracle-publishing.md) </span><span class="sxs-lookup"><span data-stu-id="00f3b-116">[Glossary of Terms for Oracle Publishing](non-sql/glossary-of-terms-for-oracle-publishing.md) </span></span>  
 [<span data-ttu-id="00f3b-117">Oracle パブリッシャーのパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="00f3b-117">Performance Tuning for Oracle Publishers</span></span>](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
