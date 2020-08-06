---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
helpviewer_keywords:
- 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3cc805042bff7259a311ca3f2acf4c26db59381b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716365"
---
# <a name="mssqlserver_50000"></a><span data-ttu-id="6be5e-102">MSSQLSERVER_50000</span><span class="sxs-lookup"><span data-stu-id="6be5e-102">MSSQLSERVER_50000</span></span>
    
## <a name="details"></a><span data-ttu-id="6be5e-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6be5e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6be5e-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6be5e-104">Product Name</span></span>|<span data-ttu-id="6be5e-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6be5e-105">SQL Server</span></span>|  
|<span data-ttu-id="6be5e-106">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="6be5e-106">Product Version</span></span>|<span data-ttu-id="6be5e-107">11.0</span><span class="sxs-lookup"><span data-stu-id="6be5e-107">11.0</span></span>|  
|<span data-ttu-id="6be5e-108">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6be5e-108">Event ID</span></span>|<span data-ttu-id="6be5e-109">50000</span><span class="sxs-lookup"><span data-stu-id="6be5e-109">50000</span></span>|  
|<span data-ttu-id="6be5e-110">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6be5e-110">Event Source</span></span>|<span data-ttu-id="6be5e-111">SETUP</span><span class="sxs-lookup"><span data-stu-id="6be5e-111">SETUP</span></span>|  
|<span data-ttu-id="6be5e-112">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6be5e-112">Component</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6be5e-113">Native Client</span><span class="sxs-lookup"><span data-stu-id="6be5e-113">Native Client</span></span>|  
|<span data-ttu-id="6be5e-114">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6be5e-114">Symbolic Name</span></span>||  
|<span data-ttu-id="6be5e-115">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6be5e-115">Message Text</span></span>|<span data-ttu-id="6be5e-116">ファイル '%.\*ls' の読み取り中にネットワーク エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6be5e-116">A network error occurred while attempting to read from the file '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6be5e-117">説明</span><span class="sxs-lookup"><span data-stu-id="6be5e-117">Explanation</span></span>  
 <span data-ttu-id="6be5e-118">名前が sqlncli.msi から変更された MSI ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client がインストールされているコンピューターで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストール (または更新) しようとしました。</span><span class="sxs-lookup"><span data-stu-id="6be5e-118">An attempt was made to install (or update) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client on a computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client is already installed, and where the existing installation was from an MSI file that was renamed from sqlncli.msi.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6be5e-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6be5e-119">User Action</span></span>  
 <span data-ttu-id="6be5e-120">このエラーを解決するには、既存のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="6be5e-120">To resolve this error, uninstall the existing version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="6be5e-121">このエラーを防ぐには、sqlncli.msi 以外の名前の MSI ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストールしないようにします。</span><span class="sxs-lookup"><span data-stu-id="6be5e-121">To prevent this error, do not install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client from an MSI file that is not named sqlncli.msi.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="6be5e-122">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="6be5e-122">Internal-Only</span></span>  
  
