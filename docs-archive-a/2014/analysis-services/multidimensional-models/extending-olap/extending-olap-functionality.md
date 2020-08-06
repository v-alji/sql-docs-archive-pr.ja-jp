---
title: OLAP 機能の拡張 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 49a17ff3-94e9-4969-84fc-37d49e63933b
author: minewiskan
ms.author: owend
ms.openlocfilehash: d64d1ac46e2571aa6f8065a8ea42e4cc43aa589e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645865"
---
# <a name="extending-olap-functionality"></a><span data-ttu-id="2a592-102">OLAP 機能の拡張</span><span class="sxs-lookup"><span data-stu-id="2a592-102">Extending OLAP functionality</span></span>
  <span data-ttu-id="2a592-103">プログラマは、複数のデータベース アプリケーションで使用および用途変更する必要がある機能を提供するアセンブリ、パーソナル化拡張機能、およびストアド プロシージャを記述して Analysis Services を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="2a592-103">As a programmer, you can extend Analysis Services by writing assemblies, personalized extensions, and stored procedures that provide functionality you want to use and repurpose in multiple database applications.</span></span> <span data-ttu-id="2a592-104">アセンブリを使用すると、新しいプロシージャや機能を MDX 言語に追加したり、パーソナル化アドインを使用したりして、多次元モデルの機能を拡張できます。</span><span class="sxs-lookup"><span data-stu-id="2a592-104">Assemblies are used to extend multidimensional models functionality by adding new procedures and functions to the MDX language or by means of the personalization addin.</span></span>  
  
 <span data-ttu-id="2a592-105">ストアド プロシージャを使用すると、外部ルーチンを呼び出すことができます。これにより、一度共通コードを開発して 1 つの場所に格納できるようになるため、Analysis Services データベースの開発および実装が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="2a592-105">Stored procedures can be used to call external routines, simplifying Analysis Services database development and implementation by allowing common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="2a592-106">ストアド プロシージャを使用して、アプリケーションに、MDX のネイティブ機能によって提供されていないビジネス機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="2a592-106">Stored procedures can be used to add business functionality to your applications that is not provided by the native functionality of MDX.</span></span>  
  
 <span data-ttu-id="2a592-107">パーソナル化は、ユーザーごとに異なる動作を提供するためにキューブに追加するカスタム オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2a592-107">Personalizations are custom objects that you add to a cube to provide a behavior that varies by user.</span></span> <span data-ttu-id="2a592-108">パーソナル化は、キューブのパーマネント オブジェクトではなく、クライアント アプリケーションがユーザーのセッション中に動的に適用するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="2a592-108">Personalizations are not permanent objects in the cube, but are objects that the client application applies dynamically during the user's session.</span></span> <span data-ttu-id="2a592-109">たとえば、データにアクセスしているユーザーに応じて金額値の通貨を変更したり、個別の KPI を提供したり、オンラインで購入する常連の顧客に合わせた提案リストを提供したりできます。</span><span class="sxs-lookup"><span data-stu-id="2a592-109">Examples include changing the currency of a monetary value depending on the person accessing the data, providing individualized KPIs, or a targeted suggestion list for regular customers who purchase online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a592-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2a592-110">In This Section</span></span>  
 [<span data-ttu-id="2a592-111">パーソナル化による OLAP の拡張</span><span class="sxs-lookup"><span data-stu-id="2a592-111">Extending OLAP through personalizations</span></span>](extending-olap-through-personalizations.md)  
  
 [<span data-ttu-id="2a592-112">Analysis Services のパーソナル化拡張機能</span><span class="sxs-lookup"><span data-stu-id="2a592-112">Analysis Services Personalization Extensions</span></span>](analysis-services-personalization-extensions.md)  
  
 [<span data-ttu-id="2a592-113">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="2a592-113">Defining Stored Procedures</span></span>](../../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
