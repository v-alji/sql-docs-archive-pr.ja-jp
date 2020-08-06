---
title: SQLXML 4.0 | のガイドラインと制限事項Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, about SQLXML
ms.assetid: fe433d30-90a1-421e-85c6-af13294dc18d
author: rothja
ms.author: jroth
ms.openlocfilehash: e020cbf0ac32e4c878b0b74b67e7c9c679d5d178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630871"
---
# <a name="guidelines-and-limitations-of-sqlxml-40"></a><span data-ttu-id="e22f9-102">SQLXML 4.0 のガイドラインと制限</span><span class="sxs-lookup"><span data-stu-id="e22f9-102">Guidelines and Limitations of SQLXML 4.0</span></span>
  <span data-ttu-id="e22f9-103">SQLXML 4.0 を使用する場合は次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e22f9-103">Remember the following when working with SQLXML 4.0:</span></span>  
  
-   <span data-ttu-id="e22f9-104">クエリ結果として返される XML は、XML を生成したマッピング スキーマに対して検証されません。</span><span class="sxs-lookup"><span data-stu-id="e22f9-104">XML returned as a query result is not validated against the mapping schema that generated the XML.</span></span>  
  
-   <span data-ttu-id="e22f9-105">SQLXML 4.0 には、バージョン固有ではない PROGID とバージョン固有の PROGID が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e22f9-105">SQLXML 4.0 includes version-independent and version-dependent PROGIDs.</span></span> <span data-ttu-id="e22f9-106">すべての実稼働アプリケーションでは、バージョン固有の PROGID を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e22f9-106">It is recommended that all production applications use version-dependent PROGIDs.</span></span> <span data-ttu-id="e22f9-107">SQLXML 4.0 には旧バージョンとの互換性は完全ではないため、これは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="e22f9-107">This is especially important because SQLXML 4.0 is not fully backward compatible.</span></span> <span data-ttu-id="e22f9-108">バージョン固有の PROGID を使用すると、新しいリリースをインストールして動作に問題が起こった場合にプログラムを保護できます。</span><span class="sxs-lookup"><span data-stu-id="e22f9-108">Using version dependent PROGIDs protects from possible production failures when you install newer releases.</span></span> <span data-ttu-id="e22f9-109">リリースが変わるたび、バグ修正や設計変更などさまざまな理由によって、プログラムの動作は変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e22f9-109">From release to release, program behavior may change for a variety of reasons, such as bug fixes, possible design changes, and so on.</span></span> <span data-ttu-id="e22f9-110">バージョン固有の PROGID を使用すると、新しいリリースをインストールして予期しないエラーが発生した場合にプログラムを保護できます。</span><span class="sxs-lookup"><span data-stu-id="e22f9-110">Using version-dependent PROGIDs protects from unexpected failure when you install newer releases.</span></span> <span data-ttu-id="e22f9-111">バージョン固有の PROGID を使用すれば、新しいバージョンのリリースをインストールしても、アプリケーションは問題なく正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="e22f9-111">With version-dependent PROGIDs, when you install a newer release, your application will continue to work without failure.</span></span> <span data-ttu-id="e22f9-112">それまで使っていたバージョン固有の PROGID を変更し、新しいリリースで最新のものを使用する場合は、実稼働する前にアプリケーションをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e22f9-112">If you decide to change the previous version-dependent PROGIDs and use the recent version-dependent PROGIDs in a newer release, you must test your application before putting it into production.</span></span> <span data-ttu-id="e22f9-113">たとえば、バージョン固有の PROGID を使用するアプリケーションでは、特定の状況下でエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e22f9-113">For example, applications using version-independent PROGIDs may fail in the following scenario:</span></span>  
  
     <span data-ttu-id="e22f9-114">つまり、SQLXML 4.0 とバージョン固有の PROGID を使用するアプリケーションを実行している状態で、他のソフトウェア プログラムをインストールすると、</span><span class="sxs-lookup"><span data-stu-id="e22f9-114">You are running an application that uses SQLXML 4.0 and version-independent PROGIDs, and you decide to install some other software program.</span></span> <span data-ttu-id="e22f9-115">このプログラムによって以前のバージョンの SQLXML がインストールされる可能性があり、</span><span class="sxs-lookup"><span data-stu-id="e22f9-115">This program might install an earlier version of SQLXML.</span></span> <span data-ttu-id="e22f9-116">この場合、アプリケーションのバージョン固有の PROGID では以前のバージョンの SQLXML が参照されるため、アプリケーションで使用する SQLXML 機能が含まれていないと、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e22f9-116">Your application may fail because the version-independent PROGIDS in your application now point to the earlier version of SQLXML, which may or may not have the SQLXML feature that your application is using.</span></span>  
  
-   <span data-ttu-id="e22f9-117">何らかの理由で SQLXMLOLEDB プロバイダーを使用せず、代わりに SQLOLEDB プロバイダーを SQLXML 機能に使用する場合は、 **Sqlxml Version**プロパティを "sqlxml. 4.0" に設定します。</span><span class="sxs-lookup"><span data-stu-id="e22f9-117">If for any reason you don't want to use the SQLXMLOLEDB provider, and instead want to use the SQLOLEDB provider for SQLXML features, set the **SQLXML Version** property to "SQLXML.4.0".</span></span>  
  
  
