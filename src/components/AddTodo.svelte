<script>
    import { todos, opc } from "../stores"

    let todo = { id: "", texto: "", estado: false };

    const addTodo = () => {
        if (!todo.texto.trim()) {
            console.log("texto vacio");
            todo.texto = "";
            return;
        }

        todo.id = Date.now();
        todos.add(todo)
        console.log($todos);
        todo = { id: "", texto: "", estado: false };

        opc.mostrar({
            texto: "todo Agregado",
            color: "bg-primary",
            estado: true
        })

       // mostrarToast("Todo agregado", "bg-primary");
    };
</script>

<form on:submit|preventDefault={addTodo}>
    <input
        type="text"
        placeholder="Enter para agregar todo"
        class="form-control shadow border-0"
        bind:value={todo.texto}
    />
</form>
