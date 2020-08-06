---
title: MSSQLSERVER_9524 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6c46ee0ef0bd1be299614e2cb04a3d6cd99d92e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640000"
---
# <a name="mssqlserver_9524"></a><span data-ttu-id="a192b-102">MSSQLSERVER_9524</span><span class="sxs-lookup"><span data-stu-id="a192b-102">MSSQLSERVER_9524</span></span>
    
## <a name="details"></a><span data-ttu-id="a192b-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a192b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a192b-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a192b-104">Product Name</span></span>|<span data-ttu-id="a192b-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a192b-105">SQL Server</span></span>|  
|<span data-ttu-id="a192b-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a192b-106">Event ID</span></span>|<span data-ttu-id="a192b-107">9254</span><span class="sxs-lookup"><span data-stu-id="a192b-107">9254</span></span>|  
|<span data-ttu-id="a192b-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a192b-108">Event Source</span></span>|<span data-ttu-id="a192b-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a192b-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a192b-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a192b-110">Component</span></span>|<span data-ttu-id="a192b-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a192b-111">SQLEngine</span></span>|  
|<span data-ttu-id="a192b-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="a192b-112">Symbolic Name</span></span>|<span data-ttu-id="a192b-113">XMLERR_INVALID_COLUMNSET_XML</span><span class="sxs-lookup"><span data-stu-id="a192b-113">XMLERR_INVALID_COLUMNSET_XML</span></span>|  
|<span data-ttu-id="a192b-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a192b-114">Message Text</span></span>|<span data-ttu-id="a192b-115">指定された XML コンテンツが、スパース列セットに必要な XML 形式に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="a192b-115">The XML content provided does not conform to the required XML format for sparse column sets.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a192b-116">説明</span><span class="sxs-lookup"><span data-stu-id="a192b-116">Explanation</span></span>  
 <span data-ttu-id="a192b-117">列セットを変更しようとしました。</span><span class="sxs-lookup"><span data-stu-id="a192b-117">An attempt was made to modify a column set.</span></span> <span data-ttu-id="a192b-118">列セットの XML コンテンツは、列セットの形式の制限を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a192b-118">The XML content of a column set must meet the format restrictions of a column set.</span></span> <span data-ttu-id="a192b-119">列セットの一般的な形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a192b-119">The general format of a column set is as follows:</span></span>  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 <span data-ttu-id="a192b-120">列セットの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックのトピック「列セットの使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a192b-120">For more information about column sets, see the topic "Using Column Sets" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a192b-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a192b-121">User Action</span></span>  
 <span data-ttu-id="a192b-122">ステートメント内の列セットの XML の形式を修正します。</span><span class="sxs-lookup"><span data-stu-id="a192b-122">Correct the format of the XML for the column set in the statement.</span></span>  
  
  
