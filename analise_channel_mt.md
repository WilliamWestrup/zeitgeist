Alguns dos caminho dos contadores parceiros na navigation

```sql
SELECT
  acc.creation_date,
  DATE_DIFF(CAST(CAST(acc.creation_date AS TIMESTAMP) as DATE),CAST(CAST(navigation_date AS TIMESTAMP) AS DATE), day) as date_diff,
  source_medium like 'google/cpc' or source_medium like '%facebook%' as media_paga,
  nav.*
FROM
  `contaazul-adhoc-data.Accountancy.analise_comportamento_navigation` AS nav
JOIN
  `contaazul-acc-data.public.accountancy` AS acc
ON
  nav.accountancy_company_id = acc.accountancy_company_id
WHERE
  nav.accountancy_company_id = 19199
ORDER BY
 navigation_created_date ASC
 ```

No caso acima, o contador teve como last click o google/cpc, antes disso passou pela pesquisa organica e direta. 
Teve contato com o facebook apenas 207 dias antes da compra.

```sql
SELECT
  acc.creation_date,
  DATE_DIFF(CAST(CAST(acc.creation_date AS TIMESTAMP) as DATE),CAST(CAST(navigation_date AS TIMESTAMP) AS DATE), day) as date_diff,
  source_medium like 'google/cpc' or source_medium like '%facebook%' as media_paga,
  nav.*
FROM
  `contaazul-adhoc-data.Accountancy.analise_comportamento_navigation` AS nav
JOIN
  `contaazul-acc-data.public.accountancy` AS acc
ON
  nav.accountancy_company_id = acc.accountancy_company_id
WHERE
  nav.accountancy_company_id = 53371
ORDER BY
  navigation_created_date ASC
```
 Nesse caso o contador teve como last_click o Branded, sendo que no dia anterior teve um contato com o google/cpc.
 Deveriamos considerar que a midia paga teve impacto direto?
