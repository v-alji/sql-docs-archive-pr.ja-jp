---
title: 省略可能な Web サービス オブジェクトの値を省略 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], omitted values
- XML Web service [Reporting Services], omitted values
- Report Server Web service, omitted values
- omitting values [Reporting Services]
ms.assetid: ceb68b8b-9214-4745-abc9-f47f33ecd6f7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3858f73e1b332acfa1a1bbc640007f6f0884abff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713814"
---
# <a name="omitting-values-for-optional-web-service-objects"></a><span data-ttu-id="9ee8a-102">オプションの Web サービス オブジェクトの値の省略</span><span class="sxs-lookup"><span data-stu-id="9ee8a-102">Omitting Values for Optional Web Service Objects</span></span>
  <span data-ttu-id="9ee8a-103">レポート サーバー Web サービス複合型のプロパティには、Specified プロパティと呼ばれる付随するプロパティを持つものがあります。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-103">Properties of several of the Report Server Web service complex types have an accompanying property known as the Specified property.</span></span> <span data-ttu-id="9ee8a-104">このプロパティには、元のプロパティ名に "Specified" が付加された名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-104">The name of the property consists of the original property name with the word "Specified" appended to it.</span></span> <span data-ttu-id="9ee8a-105">このプロパティが存在することは、元のプロパティ値が省略される可能性があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-105">The presence of this property indicates that a value for the original property may sometimes be omitted.</span></span> <span data-ttu-id="9ee8a-106">これは、Web サービス記述言語 (WSDL) から [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] のプロキシ クラスに変換した直接的な結果です。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-106">This is a direct result of the translation from the Web Service Description Language (WSDL) to a [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] proxy class.</span></span> <span data-ttu-id="9ee8a-107">たとえば、複合型 <xref:ReportService2010.DataSourceDefinition.Enabled%2A> の Web サービス プロパティ <xref:ReportService2010.DataSourceDefinition> には、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> という名前の付随するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-107">For example, the Web service property <xref:ReportService2010.DataSourceDefinition.Enabled%2A> of the complex type <xref:ReportService2010.DataSourceDefinition> has an accompanying property named <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A>.</span></span> <span data-ttu-id="9ee8a-108">アプリケーションを構築していて、<xref:ReportService2010.DataSourceDefinition.Enabled%2A> プロパティの値を設定したくない場合は、<xref:ReportService2010.DataSourceDefinition.Enabled%2A> の値を指定する必要はありません。`true` という既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-108">If you are building an application and do not want to set a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you do not have to supply a value for <xref:ReportService2010.DataSourceDefinition.Enabled%2A>; the default value of `true` is used.</span></span> <span data-ttu-id="9ee8a-109">ただし、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> は `false` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-109">However, you still need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> to `false`.</span></span> <span data-ttu-id="9ee8a-110"><xref:ReportService2010.DataSourceDefinition.Enabled%2A> プロパティの値を指定する場合は、<xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> を `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-110">If you supply a value for the <xref:ReportService2010.DataSourceDefinition.Enabled%2A> property, you need to set <xref:ReportService2010.DataSourceDefinition.EnabledSpecified%2A> equal to `true`.</span></span> <span data-ttu-id="9ee8a-111">これは書き込み可能なプロパティに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-111">This is the case for writable properties.</span></span> <span data-ttu-id="9ee8a-112">読み取り専用プロパティの場合は、アクションを行う必要がありません。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-112">For read-only properties, you do not need to take any action.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9ee8a-113">このような方法を使用したプロパティの設定に失敗すると、予想されない Web サービスの動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-113">Failure to specify a property using the above-mentioned technique can result in unpredictable Web service behavior.</span></span>  
  
 <span data-ttu-id="9ee8a-114">通常、追加で指定されたプロパティの処理を必要とするデータ型は、、、 `Boolean` `DateTime` および `Enumeration` です。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-114">The data types that usually require you to handle the additional Specified property are `Boolean`, `DateTime`, and `Enumeration`.</span></span>  
  
 <span data-ttu-id="9ee8a-115">例については、<xref:ReportService2010.ReportingService2010.CreateDataSource%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ee8a-115">For an example, see <xref:ReportService2010.ReportingService2010.CreateDataSource%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ee8a-116">参照</span><span class="sxs-lookup"><span data-stu-id="9ee8a-116">See Also</span></span>  
 <span data-ttu-id="9ee8a-117">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="9ee8a-117">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 [<span data-ttu-id="9ee8a-118">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="9ee8a-118">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  
