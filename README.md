Crear lista de productos

si usted desea solo mostrar los productos con stock positivo usar el metodo visible_on_catalog?, que esta ubicado en product.rb el metodo funciona de la 
siguiente manera 

    def visible_on_catalog? <- nombre del metodo

      self.variants.each do |variants| <- esta linea buscara en la columna stock los productos 
        if variant.stock >0            <- esta linea toma los productos con stock mayor a 0
          return true                  <- si el producto encontrado tiene stock lo mostrara
        else
          false                        <- de lo contrario no lo mostrara
        end
      end   
    end

para usar correctamente este metodo reemplazar un parte del codigo en el archivo products_controller.rb en la linea 7

    def index
      @products = Product.all <- muestra todos los productos no discrimina el stock
    end                          para usar el metodo solo cambiar .all por el nombre del
                                 metodo quedando de la siguiente forma

    def index
      @products = Product.visible_on_catalog?
    end
# desafio_ecommers_final
