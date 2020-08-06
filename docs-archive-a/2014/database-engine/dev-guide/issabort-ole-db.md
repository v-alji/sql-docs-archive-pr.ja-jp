---
title: ISSAbort (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- ISSAbort interface
ms.assetid: 7c4df482-4a83-4da0-802b-3637b507693a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7195311fefe3f0f1b7b4d6d789aa8d8487bc3bfe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742486"
---
# <a name="issabort-ole-db"></a><span data-ttu-id="a0151-102">ISSAbort (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="a0151-102">ISSAbort (OLE DB)</span></span>
  <span data-ttu-id="a0151-103">**Issabort**インターフェイスは、Native Client OLE DB プロバイダーで公開されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [Issabort:: Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)メソッドを使用して、現在の行セットを取り消すために使用されます。また、行セットを最初に生成したコマンドを使用してバッチ処理されたコマンドと、まだ実行が完了していないコマンドを取り消します。</span><span class="sxs-lookup"><span data-stu-id="a0151-103">The **ISSAbort** interface, which is exposed in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, provides the [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) method that is used to cancel the current rowset plus any commands batched with the command that initially generated the rowset, and that have not yet completed execution.</span></span>  
  
 <span data-ttu-id="a0151-104">**Issabort**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ICommand:: Execute**または**IOpenRowset:: OpenRowset**によって返される**IMultipleResults**オブジェクトに対して**QueryInterface**を使用して使用可能な Native Client プロバイダー固有のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="a0151-104">**ISSAbort** is a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client provider-specific interface available by using **QueryInterface** on the **IMultipleResults** object returned by **ICommand::Execute** or **IOpenRowset::OpenRowset**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0151-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a0151-105">In This Section</span></span>  
  
|<span data-ttu-id="a0151-106">方法</span><span class="sxs-lookup"><span data-stu-id="a0151-106">Method</span></span>|<span data-ttu-id="a0151-107">説明</span><span class="sxs-lookup"><span data-stu-id="a0151-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0151-108">ISSAbort:: Abort &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a0151-108">ISSAbort::Abort &#40;OLE DB&#41;</span></span>](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md)|<span data-ttu-id="a0151-109">現在の行セットと、現在のコマンドに関連付けられているバッチ コマンドを取り消します。</span><span class="sxs-lookup"><span data-stu-id="a0151-109">Cancels the current rowset plus any batched commands associated with the current command.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0151-110">参照</span><span class="sxs-lookup"><span data-stu-id="a0151-110">See Also</span></span>  
 [<span data-ttu-id="a0151-111">インターフェイス &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a0151-111">Interfaces &#40;OLE DB&#41;</span></span>](../../../2014/database-engine/dev-guide/interfaces-ole-db.md)  
  
  
