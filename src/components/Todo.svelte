<script>
    import { todos,opc } from "../stores"
    
    export let item;

    const delTodo = (id) => {
        todos.delete(id)
        opc.mostrar({
            texto: "todo Eliminado",
            color: "bg-danger",
            estado: true
        })
       // mostrarToast("Todo eliminado", "bg-danger");
    };

    const editTodo = (id) => {
        todos.put(id)
        console.log(todos);
        opc.mostrar({
            texto: "todo Editado",
            color: "bg-warning",
            estado: true
        })
       // mostrarToast("Todo editado", "bg-warning");
    };

    const classIcono = (valor) =>
        valor ? "bi bi-arrow-clockwise" : "bi bi-check2";
    const classEstado = (valor) => (valor ? "btn-success" : "btn-warning");
</script>

<div class="shadow my-3 p-3 lead">
    <p class={item.estado ? "text-decoration-line-through" : ""}>
        {item.texto}
    </p>

    <button
        class="btn btn-sm {classEstado(item.estado)}"
        on:click={editTodo(item.id)}
    >
        <i class={classIcono(item.estado)} />
    </button>

    <button class="btn btn-sm btn-danger" on:click={delTodo(item.id)}>
        <i class="bi bi-trash" />
    </button>
</div>
