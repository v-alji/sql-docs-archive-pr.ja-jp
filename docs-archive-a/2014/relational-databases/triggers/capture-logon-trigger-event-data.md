---
title: ログオン トリガーのイベント データのキャプチャ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e05b1ab4-c10b-402a-9591-f6ec1e3db8c0
author: rothja
ms.author: jroth
ms.openlocfilehash: b11323702d7468d07783b4d1c763dba691479d9c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644913"
---
# <a name="capture-logon-trigger-event-data"></a><span data-ttu-id="f32b3-102">ログオン トリガーのイベント データのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="f32b3-102">Capture Logon Trigger Event Data</span></span>
  <span data-ttu-id="f32b3-103">ログオン トリガー内で使用するために LOGON イベントに関する XML データをキャプチャするには、 [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-103">To capture XML data about LOGON events for use inside logon triggers, use the [EVENTDATA](/sql/t-sql/functions/eventdata-transact-sql) function.</span></span> <span data-ttu-id="f32b3-104">LOGON イベントは、次のイベントのデータ スキーマを返します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-104">The LOGON event returns the following event data schema:</span></span>  
  
 `<EVENT_INSTANCE>`  
  
 `<EventType>event_type</EventType>`  
  
 `<PostTime>post_time</PostTime>`  
  
 `<SPID>spid</SPID>`  
  
 `<ServerName>server_name</ServerName>`  
  
 `<LoginName>login_name</LoginName>`  
  
 `<LoginType>login_type</LoginType>`  
  
 `<SID>sid</SID>`  
  
 `<ClientHost>client_host</ClientHost>`  
  
 `<IsPooled>is_pooled</IsPooled>`  
  
 `</EVENT_INSTANCE>`  
  
 `<EventType>`  
 <span data-ttu-id="f32b3-105">`LOGON`を格納します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-105">Contains `LOGON`.</span></span>  
  
 `<PostTime>`  
 <span data-ttu-id="f32b3-106">セッションの確立が要求される時刻を格納します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-106">Contains the time when a session is requested to be established.</span></span>  
  
 `<SID>`  
 <span data-ttu-id="f32b3-107">指定されたログイン名のセキュリティ ID 番号 (SID) の Base 64 エンコード形式のバイナリ ストリームを格納します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-107">Contains the base 64-encoded binary stream of the security identification number (SID) for the specified login name.</span></span>  
  
 `<ClientHost>`  
 <span data-ttu-id="f32b3-108">接続を確立したクライアントのホスト名を格納します。</span><span class="sxs-lookup"><span data-stu-id="f32b3-108">Contains the host name of the client from where the connection is made.</span></span> <span data-ttu-id="f32b3-109">クライアントとサーバーの名前が同じ場合、この値は '`<local_machine>`' になります。</span><span class="sxs-lookup"><span data-stu-id="f32b3-109">The value is '`<local_machine>`' if the client and server name are the same.</span></span> <span data-ttu-id="f32b3-110">これらの名前が異なる場合、この値はクライアントの IP アドレスになります。</span><span class="sxs-lookup"><span data-stu-id="f32b3-110">Otherwise, the value is the IP address of the client.</span></span>  
  
 `<IsPooled>`  
 <span data-ttu-id="f32b3-111">接続プールを使用して接続が再利用される場合は `1` になります。</span><span class="sxs-lookup"><span data-stu-id="f32b3-111">Is `1` if the connection is reused by using connection pooling.</span></span> <span data-ttu-id="f32b3-112">それ以外の場合、値は `0`に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f32b3-112">Otherwise, the value is `0`.</span></span>  
  
  
