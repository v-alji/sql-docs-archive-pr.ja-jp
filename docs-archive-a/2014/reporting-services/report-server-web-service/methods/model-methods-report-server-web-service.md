---
title: モデルメソッド |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
ms.assetid: d3e658c9-bb22-480b-a3d5-bcde8f537ab2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0b93b43383a4b0e5bf19d7c6be9c415d7c91e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721086"
---
# <a name="model-methods"></a><span data-ttu-id="59285-102">モデルのメソッド</span><span class="sxs-lookup"><span data-stu-id="59285-102">Model Methods</span></span>
  <span data-ttu-id="59285-103">これらのメソッドを使用して、モデルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="59285-103">You can use these methods to manage models.</span></span>  
  
|<span data-ttu-id="59285-104">Method</span><span class="sxs-lookup"><span data-stu-id="59285-104">Method</span></span>|<span data-ttu-id="59285-105">アクション</span><span class="sxs-lookup"><span data-stu-id="59285-105">Action</span></span>|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GenerateModel%2A>|<span data-ttu-id="59285-106">共有データ ソース上に既定のモデルを生成します。</span><span class="sxs-lookup"><span data-stu-id="59285-106">Generates a default model on top of a shared data source.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPermissions%2A>|<span data-ttu-id="59285-107">モデル アイテムに関連付けられたユーザー アクセス許可を取得します。</span><span class="sxs-lookup"><span data-stu-id="59285-107">Retrieves the user permissions that are associated with the model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetModelItemPolicies%2A>|<span data-ttu-id="59285-108">モデル アイテムに関連付けられたポリシーを取得します。</span><span class="sxs-lookup"><span data-stu-id="59285-108">Retrieves the policies that are associated with a model item.</span></span>|  
|<xref:ReportService2010.ReportingService2010.GetUserModel%2A>|<span data-ttu-id="59285-109">現在のユーザーのモデルのセマンティック部分を返します。</span><span class="sxs-lookup"><span data-stu-id="59285-109">Returns the semantic piece of a model for the current user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.InheritModelItemParentSecurity%2A>|<span data-ttu-id="59285-110">モデル アイテムに関連付けられたポリシーを削除します。これにより、モデル アイテムは親からポリシーを継承します。</span><span class="sxs-lookup"><span data-stu-id="59285-110">Deletes the policies that are associated with a model item and causes the model item to inherit the policies from its parent.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelDrillthroughReports%2A>|<span data-ttu-id="59285-111">モデル内のエンティティに関連付けられた詳細レポートの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="59285-111">Lists drillthrough reports that are associated with an entity in a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemChildren%2A>|<span data-ttu-id="59285-112">モデル アイテムの子要素の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="59285-112">Returns an array of model item child elements.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelItemTypes%2A>|<span data-ttu-id="59285-113">サポートされているモデル アイテムの種類の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="59285-113">Returns a list of supported model item types.</span></span>|  
|<xref:ReportService2010.ReportingService2010.ListModelPerspectives%2A>|<span data-ttu-id="59285-114">ユーザーが利用できるモデルとパースペクティブの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="59285-114">Lists models and perspectives that are available to the user.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RegenerateModel%2A>|<span data-ttu-id="59285-115">データ ソース スキーマの変更に基づいて既存のモデルを更新します。</span><span class="sxs-lookup"><span data-stu-id="59285-115">Updates an existing model based on changes to the data source schema.</span></span>|  
|<xref:ReportService2010.ReportingService2010.RemoveAllModelItemPolicies%2A>|<span data-ttu-id="59285-116">指定したモデル内のモデル アイテムに関連付けられたすべてのポリシーを削除します。</span><span class="sxs-lookup"><span data-stu-id="59285-116">Deletes all policies that are associated with model items in the specified model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelDrillthroughReports%2A>|<span data-ttu-id="59285-117">一連の詳細レポートをモデルに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="59285-117">Associates a set of drillthrough reports together with a model.</span></span>|  
|<xref:ReportService2010.ReportingService2010.SetModelItemPolicies%2A>|<span data-ttu-id="59285-118">モデル アイテムにセキュリティ ポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="59285-118">Sets security policies on a model item.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59285-119">参照</span><span class="sxs-lookup"><span data-stu-id="59285-119">See Also</span></span>  
 <span data-ttu-id="59285-120">[Web サービスと .NET Framework を使用してのアプリケーションの構築](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="59285-120">[Building Applications Using the Web Service and the .NET Framework](../net-framework/building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="59285-121">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="59285-121">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 <span data-ttu-id="59285-122">[レポート サーバー Web サービス メソッド](report-server-web-service-methods.md) </span><span class="sxs-lookup"><span data-stu-id="59285-122">[Report Server Web Service Methods](report-server-web-service-methods.md) </span></span>  
 [<span data-ttu-id="59285-123">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="59285-123">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
