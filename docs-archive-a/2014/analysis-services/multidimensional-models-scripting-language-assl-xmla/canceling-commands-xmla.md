---
title: コマンドのキャンセル (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- connections [XML for Analysis]
- associated connections [XML for Analysis]
- XML for Analysis, canceling
- associated sessions [XML for Analysis]
- canceling connections
- canceling commands
- canceling sessions
- SPID
- XMLA, canceling
- server process IDs [XML for Analysis]
- sessions [XML for Analysis]
ms.assetid: b59f8197-c33d-4e65-9022-848ccba540f5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 003c70362c38ae1838b4679abf6485fa031a9143
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712581"
---
# <a name="canceling-commands-xmla"></a><span data-ttu-id="60d3c-102">コマンドのキャンセル (XMLA)</span><span class="sxs-lookup"><span data-stu-id="60d3c-102">Canceling Commands (XMLA)</span></span>
  <span data-ttu-id="60d3c-103">コマンドを発行するユーザーの管理アクセス許可によっては、XML for Analysis (XMLA) の[Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla)コマンドを使用して、セッション、セッション、接続、サーバープロセス、または関連付けられたセッションまたは接続に対してコマンドを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-103">Depending on the administrative permissions of the user issuing the command, the [Cancel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/cancel-element-xmla) command in XML for Analysis (XMLA) can cancel a command on a session, a session, a connection, a server process, or an associated session or connection.</span></span>  
  
## <a name="canceling-commands"></a><span data-ttu-id="60d3c-104">コマンドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-104">Canceling Commands</span></span>  
 <span data-ttu-id="60d3c-105">プロパティを指定せずに `Cancel` コマンドを送信することにより、ユーザーは現在の明示的なセッションのコンテキスト内で現在実行中のコマンドをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-105">A user can cancel the currently executing command within the context of the current explicit session by sending a `Cancel` command with no specified properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60d3c-106">暗黙のセッション内で実行中のコマンドは、ユーザー操作によって取り消すことはできません。</span><span class="sxs-lookup"><span data-stu-id="60d3c-106">A command running in an implicit session cannot be canceled by a user.</span></span>  
  
### <a name="canceling-batch-commands"></a><span data-ttu-id="60d3c-107">バッチ コマンドのキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-107">Canceling Batch Commands</span></span>  
 <span data-ttu-id="60d3c-108">ユーザーが `Batch` コマンドを取り消した場合、`Batch` コマンド内に残っている未実行のコマンドはすべて取り消されます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-108">If a user cancels a `Batch` command, then all remaining commands not yet executed within the `Batch` command are canceled.</span></span> <span data-ttu-id="60d3c-109">`Batch` コマンドがトランザクション型であれば、`Cancel` コマンドの実行前に実行されたすべてのコマンドはロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-109">If the `Batch` command was transactional, any commands that were executed before the `Cancel` command runs are rolled back.</span></span>  
  
## <a name="canceling-sessions"></a><span data-ttu-id="60d3c-110">セッションのキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-110">Canceling Sessions</span></span>  
 <span data-ttu-id="60d3c-111">コマンドの[SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)プロパティに明示的なセッションのセッション識別子を指定することによって `Cancel` 、データベース管理者またはサーバー管理者は、現在実行中のコマンドを含め、セッションを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-111">By specifying a session identifier for an explicit session in the [SessionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a database administrator or server administrator can cancel a session, including the currently executing command.</span></span> <span data-ttu-id="60d3c-112">データベース管理者は、自分が管理権限を持つデータベースに対するセッションだけをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-112">A database administrator can only cancel sessions for databases on which he or she has administrative permissions.</span></span>  
  
 <span data-ttu-id="60d3c-113">データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得することにより、指定されたデータベースに対するアクティブ セッションを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-113">A database administrator can retrieve the active sessions for a specified database by retrieving the DISCOVER_SESSIONS schema rowset.</span></span> <span data-ttu-id="60d3c-114">データベース管理者は、DISCOVER_SESSIONS スキーマ行セットを取得するために、XMLA メソッドを使用 `Discover` して、メソッドの restriction プロパティの[Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) SESSION_CURRENT_DATABASE restriction 列に適切なデータベース識別子を指定し `Discover` ます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-114">To retrieve the DISCOVER_SESSIONS schema rowset, the database administrator uses the XMLA `Discover` method and specifies the appropriate database identifier for the SESSION_CURRENT_DATABASE restriction column in the [Restrictions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictions-element-xmla) property of the `Discover` method.</span></span>  
  
## <a name="canceling-connections"></a><span data-ttu-id="60d3c-115">接続のキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-115">Canceling Connections</span></span>  
 <span data-ttu-id="60d3c-116">コマンドの[ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla)プロパティで接続識別子を指定することにより、 `Cancel` サーバー管理者は、実行中のすべてのコマンドを含め、特定の接続に関連付けられているすべてのセッションをキャンセルし、接続を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-116">By specifying a connection identifier in the [ConnectionID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/connectionid-element-xmla) property of the `Cancel` command, a server administrator can cancel all of the sessions associated with a given connection, including all running commands, and cancel the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60d3c-117">のインスタンスが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続に関連付けられたセッションを特定およびキャンセルできない場合 (HTTP 接続を提供している間にデータポンプが複数のセッションを開いた場合など)、インスタンスは接続を取り消すことができません。</span><span class="sxs-lookup"><span data-stu-id="60d3c-117">If the instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cannot locate and cancel the sessions associated with a connection, such as when the data pump opens multiple sessions while providing HTTP connectivity, the instance cannot cancel the connection.</span></span> <span data-ttu-id="60d3c-118">`Cancel` コマンドの実行中にこのような状況が生じた場合には、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="60d3c-118">If this case is encountered during the execution of a `Cancel` command, an error occurs.</span></span>  
  
 <span data-ttu-id="60d3c-119">サーバー管理者は XMLA の `Discover` メソッドを使用して DISCOVER_CONNECTIONS スキーマ行セットを取得することにより、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのアクティブな接続を取得できます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-119">A server administrator can retrieve the active connections for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance by retrieving the DISCOVER_CONNECTIONS schema rowset using the XMLA `Discover` method.</span></span>  
  
## <a name="canceling-server-processes"></a><span data-ttu-id="60d3c-120">サーバー プロセスのキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-120">Canceling Server Processes</span></span>  
 <span data-ttu-id="60d3c-121">サーバー管理者は、コマンドの[spid](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)プロパティにサーバープロセス識別子 (spid) を指定することにより、 `Cancel` 特定の spid に関連付けられているコマンドを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-121">By specifying a server process identifier (SPID) in the [SPID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) property of the `Cancel` command, a server administrator can cancel the commands associated with a given SPID.</span></span>  
  
## <a name="canceling-associated-sessions-and-connections"></a><span data-ttu-id="60d3c-122">関連するセッションおよび接続のキャンセル</span><span class="sxs-lookup"><span data-stu-id="60d3c-122">Canceling Associated Sessions and Connections</span></span>  
 <span data-ttu-id="60d3c-123">[Cancelassociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla)プロパティを true に設定すると、コマンドで指定された接続、セッション、または SPID に関連付けられている接続、セッション、およびコマンドを取り消すことができ `Cancel` ます。</span><span class="sxs-lookup"><span data-stu-id="60d3c-123">You can set the [CancelAssociated](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cancelassociated-element-xmla) property to true to cancel the connections, sessions, and commands associated with the connection, session, or SPID specified in the `Cancel` command.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d3c-124">参照</span><span class="sxs-lookup"><span data-stu-id="60d3c-124">See Also</span></span>  
 <span data-ttu-id="60d3c-125">[XMLA&#41;&#40;Discover メソッド](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span><span class="sxs-lookup"><span data-stu-id="60d3c-125">[Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) </span></span>  
 [<span data-ttu-id="60d3c-126">Analysis Services での XMLA による開発</span><span class="sxs-lookup"><span data-stu-id="60d3c-126">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
