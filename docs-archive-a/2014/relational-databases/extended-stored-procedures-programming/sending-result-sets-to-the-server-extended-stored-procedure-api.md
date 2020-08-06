---
title: 結果セットのサーバーへの送信 (拡張ストアドプロシージャ API) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
ms.openlocfilehash: 82984440f96416189eb18f900764ee7bdaf05a01
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631030"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a><span data-ttu-id="2c0d9-102">結果セットのサーバーへの送信 (拡張ストアド プロシージャ API)</span><span class="sxs-lookup"><span data-stu-id="2c0d9-102">Sending Result Sets to the Server (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2c0d9-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="2c0d9-104">結果セットをに送信する場合 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、拡張ストアドプロシージャは次のように適切な API を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-104">When sending a result set to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the extended stored procedure should call the appropriate API as follows:</span></span>  
  
-   <span data-ttu-id="2c0d9-105">**Srv_sendmsg**関数は、すべての行 (存在する場合) が**srv_sendrow**と共に送信される前または後に、任意の順序で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-105">The **srv_sendmsg** function may be called in any order before or after all rows (if any) have been sent with **srv_sendrow**.</span></span> <span data-ttu-id="2c0d9-106">完了ステータスが**srv_senddone**と共に送信される前に、すべてのメッセージをクライアントに送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-106">All messages must be sent to the client before the completion status is sent with **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="2c0d9-107">**srv_sendrow** 関数は、クライアントに送信される各行につき 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-107">The **srv_sendrow** function is called once for each row sent to the client.</span></span> <span data-ttu-id="2c0d9-108">すべての行は、メッセージ、状態値、または完了状態を**srv_sendmsg**と共に送信する前にクライアントに送信する必要があります。また、 **srv_pfield**または**srv_senddone**の**srv_status**引数を使用して送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-108">All rows must be sent to the client before any messages, status values, or completion statuses are sent with **srv_sendmsg**, the **srv_status** argument of **srv_pfield**, or **srv_senddone**.</span></span>  
  
-   <span data-ttu-id="2c0d9-109">**Srv_describe**ですべての列が定義されていない行を送信すると、アプリケーションで情報エラーメッセージが生成され、クライアントに FAIL が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-109">Sending a row that has not had all its columns defined with **srv_describe** causes the application to raise an informational error message and return FAIL to the client.</span></span> <span data-ttu-id="2c0d9-110">この場合、その行は送信されません。</span><span class="sxs-lookup"><span data-stu-id="2c0d9-110">In this case, the row is not sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0d9-111">参照</span><span class="sxs-lookup"><span data-stu-id="2c0d9-111">See Also</span></span>  
 [<span data-ttu-id="2c0d9-112">拡張ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="2c0d9-112">Creating Extended Stored Procedures</span></span>](creating-extended-stored-procedures.md)  
  
  
