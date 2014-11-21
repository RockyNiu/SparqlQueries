SparqlQueries
=============
####count 
<pre><code>
#### count
select (count (*) as ?count)
where
{
	#graph <>
	{
		?s ?p ?o.
	}
}
</code></pre>
####list graphs
<pre><code>
##### list graphs
select ?g
where
{
	graph ?g {?s ?p ?o.}
}
</code></pre>
####move triples from one graph to another graph
<pre><code>
##### move triples from one graph to another graph
insert
{
	graph <http://test/>
	{?s ?p ?o}
}
where
{
	graph <http://>
	{?s ?p ?o}
};
drop graph <http://>;
</code></pre>
####find a key word
<pre><code>
#### find a key word
select distinct ?s ?p ?o
where
{
	#graph <>
	{
		?s ?p ?o .
		filter (regex(str(?s), 'person','i') || regex(str(?p), 'person','i') || regex(str(?o), 'person','i'))
	}
}
</code></pre>
