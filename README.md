use Chinook_AutoIncrement
go

--Parte 1

--item I
SELECT ar.Name AS artista, al.Title AS album, t.Name AS faixa
FROM Track AS t
INNER JOIN Album AS al
	ON t.AlbumId = al.AlbumId
INNER JOIN Artist AS ar
	ON al.ArtistId = ar.ArtistId
WHERE ar.Name = N'Cássia Eller'
ORDER BY al.Title, t.Name;

-- Pergunta 1: ela devolve o nome dos artistista dentro da tabela artist, os titulos da tabela Album, e os nomes das faixa da tabela Track
-- 1° linha usa o select pra devolver, 2° usa o from pra pra indicar de onde o select vai tirar as informações, os inner join servem pra link e os as serve pra trocar o nome, on pra linkar od ids, where pra mostrar onde os dados vao ser buscados e oder by pra mostrar a ondem da devolução

select * from Customer;
select * from Employee;
select * from Invoice;

--Item II
--Pergunta 2 : steve
select c.FirstName, c.SupportRepId, em.FirstName
from Customer as c
inner join Employee as em
	on c.SupportRepId = em.EmployeeId
where (c.Country = 'United Kingdom')

--item III
select i.InvoiceId, c.FirstName as cliente,
	CONVERT(VARCHAR(10), InvoiceDate, 103)
		AS data_br,
	Total
from Invoice as i
inner join Customer as c
	on c.CustomerId = i.CustomerId
where (c.Country = 'United Kingdom')
order by InvoiceDate

--item IV
SELECT COUNT(*) AS nota_Total
FROM Invoice
WHERE BillingCountry = 'United Kingdom';

--item V

--item VI
--Pergunta 3: sim, vieram 3 linhas, precisava ser 21, o erro é que o on estava coparando o invoice id com customer id
SELECT c.FirstName, c.LastName, i.InvoiceId, i.Total
FROM Customer AS c
INNER JOIN Invoice AS i
	ON i.CustomerId = c.CustomerId
WHERE c.Country = 'United Kingdom';
