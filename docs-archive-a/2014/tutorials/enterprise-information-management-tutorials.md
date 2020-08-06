---
title: Enterprise Information Management チュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8cde162479645ab13a6ae000cc46e42e3c10e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643045"
---
# <a name="enterprise-information-management-tutorials"></a><span data-ttu-id="776a0-102">Enterprise Information Management のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="776a0-102">Enterprise Information Management Tutorials</span></span>
  <span data-ttu-id="776a0-103">このセクションには、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] に付属の Enterprise Information Management (EIM) テクノロジを使用して、企業で情報を管理する方法のチュートリアルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="776a0-103">This section contains tutorials for managing information in an enterprise by using Enterprise Information Management (EIM) technologies that are included in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span> <span data-ttu-id="776a0-104">Enterprise Integration Management (EIM) では、組織がデータの信頼性と一貫性を信頼してビジネス上の重要な意思決定を行うことを可能にするソリューションのポートフォリオが用意されています。</span><span class="sxs-lookup"><span data-stu-id="776a0-104">Enterprise Integration Management (EIM) provides a portfolio of solutions that enable organizations to trust the credibility and consistency of their data so they can make critical business decisions.</span></span> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="776a0-105">には、企業で EIM ソリューションを実装する際に役立つ以下のテクノロジがあります。</span><span class="sxs-lookup"><span data-stu-id="776a0-105">has the following technologies that help you implement EIM solutions in your enterprise.</span></span>  
  
-   <span data-ttu-id="776a0-106">SQL Server Integration Services (SSIS)。</span><span class="sxs-lookup"><span data-stu-id="776a0-106">SQL Server Integration Services (SSIS).</span></span> <span data-ttu-id="776a0-107">SSIS では、ビジネス ワークフロー、データ ウェアハウス、またはマスター データ管理をサポートする包括的な抽出、変換、および読み込み (ETL) のさまざまなソースからデータを統合するための強力な拡張可能プラットフォームを用意しています。</span><span class="sxs-lookup"><span data-stu-id="776a0-107">SSIS provides a powerful, extensible platform for integrating data from various sources in a comprehensive extract, transform, and load (ETL) solution that supports business workflows, a data warehouse, or master data management.</span></span>  
  
-   <span data-ttu-id="776a0-108">SQL Server Data Quality Services (DQS)。</span><span class="sxs-lookup"><span data-stu-id="776a0-108">SQL Server Data Quality Services (DQS).</span></span> <span data-ttu-id="776a0-109">DQS ではデータのクレンジング、照合、標準化、および拡充が可能なため、ビジネス インテリジェンス、データ ウェアハウス、およびトランザクション処理ワークロードに対して信頼できる情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="776a0-109">DQS enables you to cleanse, match, standardize, and enrich data, so you can deliver trusted information for business intelligence, a data warehouse, and transaction processing workloads.</span></span>  
  
-   <span data-ttu-id="776a0-110">SQL Server マスター データ サービス (MDS)。</span><span class="sxs-lookup"><span data-stu-id="776a0-110">SQL Server Master Data Services (MDS).</span></span> <span data-ttu-id="776a0-111">MDS の中央データ ハブは、情報の整合性とデータの一貫性がアプリケーション間で変化していないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="776a0-111">MDS provides a central data hub that ensures that the integrity of information and consistency of data is constant across different applications.</span></span>  
  
 [<span data-ttu-id="776a0-112">SSIS、MDS、DQS を組み合わせたエンタープライズ情報管理 &#91;チュートリアル&#93;</span><span class="sxs-lookup"><span data-stu-id="776a0-112">Enterprise Information Management using SSIS, MDS, and DQS Together &#91;Tutorial&#93;</span></span>](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 <span data-ttu-id="776a0-113">このチュートリアルでは、SSIS、MDS、および DQS を組み合わせて、Enterprise Information Management (EIM) ソリューションのサンプルを実装する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="776a0-113">In this tutorial, you learn how to use SSIS, MDS, and DQS together to implement a sample Enterprise Information Management (EIM) solution.</span></span> <span data-ttu-id="776a0-114">まず、DQS を使用して仕入先データ (メタデータ) についてのナレッジを含むナレッジ ベースを作成し、ナレッジ ベースに対して Excel ファイル内のデータをクレンジングして、データ内の重複項目を特定および削除するようにデータを照合します。</span><span class="sxs-lookup"><span data-stu-id="776a0-114">First, you use DQS to create a knowledgebase with the knowledge about the supplier data (metadata), cleanse the data in an Excel file against the knowledge base, and match the data to identify and remove duplicates in the data.</span></span> <span data-ttu-id="776a0-115">次に、Excel 用の MDS アドインを使用して、クレンジングおよび照合済みのデータを MDS にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="776a0-115">Next, you use the MDS Add-in for Excel to upload the cleansed and matched data to MDS.</span></span> <span data-ttu-id="776a0-116">次に、SSIS ソリューションを使用して全体のプロセスを自動化します。</span><span class="sxs-lookup"><span data-stu-id="776a0-116">Then, you automate the whole process by using an SSIS solution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="776a0-117">参照</span><span class="sxs-lookup"><span data-stu-id="776a0-117">See Also</span></span>  
 [<span data-ttu-id="776a0-118">エンタープライズ情報管理-Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="776a0-118">Enterprise Information Management - Microsoft SQL Server</span></span>](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
