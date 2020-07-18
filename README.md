# DataMapper

A macro module and behaviour with default mapping implementations.

Documentation can be generated with [ExDoc](https://github.com/elixir-lang/ex_doc)
and published on [HexDocs](https://hexdocs.pm). Once published, the docs can
be found at [https://hexdocs.pm/data_mapper](https://hexdocs.pm/data_mapper).


## Installation

If [available in Hex](https://hex.pm/docs/publish), the package can be installed
by adding `data_mapper` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:data_mapper, "~> 0.1.0"}
  ]
end
```

## Usage

```elixir
defmodule FooMapper do
  @moduledoc """
  Map the Foo external data to our own data structures.
  """
  use DataMapper,
    mappings: %{
      "someFoo" => :foo,
      "someBar" => :bar,
      "extraThing" => :extra_thing
    }

  @impl DataMapper

  def map_field({_, nil} = field), do: field

  def map_field({:bar, field}) do
    {:bar, field * 1000}
  end

  def map_field(field), do: field
end
```