VERSÃO SIMPLES

Esta versão faz apenas:
- abrir chamado
- listar chamados

CONFIGURAÇÃO
1. Abra o arquivo supabase.js
2. Preencha:
   const SUPABASE_URL = "https://SEU-PROJETO.supabase.co";
   const SUPABASE_KEY = "SUA_ANON_KEY";

3. Rode:
   python -m http.server 8000

4. Abra:
   http://localhost:8000

SQL DA TABELA

create table if not exists chamados (
  id text primary key,
  nome text,
  unidade text,
  setor text,
  setor_problema text,
  tipo_manutencao text,
  gravidade text,
  descricao text,
  foto_url text,
  status text,
  data_criacao timestamptz
);

alter table chamados enable row level security;

create policy "public insert"
on chamados for insert to anon with check (true);

create policy "public select"
on chamados for select to anon using (true);
