---
title: OLEDB イベント カテゴリ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- OLEDB event category
- SQL Server event classes, OLEDB event category
- event classes [SQL Server], OLEDB event category
ms.assetid: cf93e424-3dac-462d-b3da-92e7d0b064d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd55294966448f8976dc20198381918e163cc0d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633858"
---
# <a name="oledb-event-category"></a><span data-ttu-id="178d2-102">OLEDB イベント カテゴリ</span><span class="sxs-lookup"><span data-stu-id="178d2-102">OLEDB Event Category</span></span>
  <span data-ttu-id="178d2-103">**OLEDB** イベント カテゴリには、一般的な OLEDB イベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="178d2-103">The **OLEDB** event category contains general OLEDB events.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="178d2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="178d2-104">In This Section</span></span>  
  
|<span data-ttu-id="178d2-105">トピック</span><span class="sxs-lookup"><span data-stu-id="178d2-105">Topic</span></span>|<span data-ttu-id="178d2-106">説明</span><span class="sxs-lookup"><span data-stu-id="178d2-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="178d2-107">OLEDB Call イベント クラス</span><span class="sxs-lookup"><span data-stu-id="178d2-107">OLEDB Call Event Class</span></span>](oledb-call-event-class.md)|<span data-ttu-id="178d2-108">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、分散クエリとリモート ストアド プロシージャ用の OLE DB プロバイダーに、データ以外の呼び出しまたは **QueryInterface** ではない呼び出しが行われたことを示します。</span><span class="sxs-lookup"><span data-stu-id="178d2-108">Indicates that [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has made a non-data or non-**QueryInterface** call to an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="178d2-109">OLEDB DataRead イベント クラス</span><span class="sxs-lookup"><span data-stu-id="178d2-109">OLEDB DataRead Event Class</span></span>](oledb-dataread-event-class.md)|<span data-ttu-id="178d2-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって分散クエリとリモート ストアド プロシージャの OLE DB プロバイダーが呼び出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="178d2-110">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has called an OLE DB provider for distributed queries and remote stored procedures.</span></span>|  
|[<span data-ttu-id="178d2-111">OLEDB Errors イベント クラス</span><span class="sxs-lookup"><span data-stu-id="178d2-111">OLEDB Errors Event Class</span></span>](oledb-errors-event-class.md)|<span data-ttu-id="178d2-112">OLE DB プロバイダーへの呼び出しで、エラーが返されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="178d2-112">Indicates that a call to an OLE DB provider returned an error.</span></span>|  
|[<span data-ttu-id="178d2-113">OLEDB Provider Information イベント クラス</span><span class="sxs-lookup"><span data-stu-id="178d2-113">OLEDB Provider Information Event Class</span></span>](oledb-provider-information-event-class.md)|<span data-ttu-id="178d2-114">分散クエリが実行され、プロバイダー接続に対応する情報が収集されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="178d2-114">Indicates that a distributed query has run and has collected information that corresponds to the provider connection.</span></span>|  
|[<span data-ttu-id="178d2-115">OLEDB QueryInterface イベント クラス</span><span class="sxs-lookup"><span data-stu-id="178d2-115">OLEDB QueryInterface Event Class</span></span>](oledb-queryinterface-event-class.md)|<span data-ttu-id="178d2-116">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって分散クエリとリモート ストアド プロシージャに対する OLE DB **QueryInterface** 呼び出しが発行されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="178d2-116">Indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued an OLE DB **QueryInterface** call for distributed queries and remote stored procedures.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="178d2-117">参照</span><span class="sxs-lookup"><span data-stu-id="178d2-117">See Also</span></span>  
 [<span data-ttu-id="178d2-118">拡張イベント</span><span class="sxs-lookup"><span data-stu-id="178d2-118">Extended Events</span></span>](../extended-events/extended-events.md)  
  
  
