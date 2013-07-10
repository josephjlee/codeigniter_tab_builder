Codeigniter Tab Builder
=======================

CodeIgniter library to build uniform tab elements with bootstrap styling.

Functions
=========

add_tabs($tabs)
---------------
* **$tabs** array adds a new tab. array must contain **id** and **name**.

start_tab()
-----------
starts the wrapper for all the tab contents

start_tab_content($id, $is_active)
----------------------------------
starts the content of a specific tab.
* **$id** string refers to the tab id, that will be activated upon click.
* **$is_active** boolean whether the tab should be shown at first

end_tab_content()
-----------------
ends the specific tab content.

end_tab()
---------
ends all tab contents all together.

Example
=======


within the controller:

    $this->load->library('tab_builder');
    
within the view:

    <?php
      // could also be passed from the controller
      $_tabs = array();
      foreach (array(1, 2, 3) as $idx) {
        array_push($_tabs, array('id' => "tabContract{$idx}", 'name' => "Tab {$idx}"));
      }
      $this->tab_builder->add_tabs($_tabs);
    ?>
    
    <?php
      $this->tab_builder->start_tab();
      
      foreach (array(1, 2, 3) as $idx) {
  		  $this->tab_builder->start_tab_content("tab{$target->contract_id}", ($idx == 1));
    ?>
    
    <div>
      tab content <?php echo $idx;?>
    </div>
    
    <?php
        $this->tab_builder->end_tab_content();
      } // end foreach
      
      $this->tab_builder->end_tab();
    ?>
