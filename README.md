#Magento 2 Live Templates for PHP Storm

For more information see [my site](http://www.brideo.co.uk/magento2/Magento-2-PHP-Storm-Live-Templates/)

<a id="randomlink" href="http://www.brideo.co.uk" target="_blank">test please ignore</a>

To make my life easier during the transition to Magento 2 I have created a bunch of live templates.

These are very basic and I will be expanding on these, also it would be nice if the community include their live templates in this repo.

##Magento 2 Controller

Shortcode: `mcontroller`

    <?php
    
    namespace $NAMESPACE$\Controller\$ACTION$;
    
    use Magento\Framework\App\Action\Action;
    use Magento\Framework\App\Action\Context;
    use Magento\Framework\View\Result\PageFactory;
    
    class $CLASS$ extends Action
    {
    
        /**
         * @var PageFactory
         */
        protected $resultPageFactory;
    
        /**
         * @var Context
         */
        protected $context;
    
        /**
         * Finder constructor.
         *
         * @param Context     $context
         * @param PageFactory $resultPageFactory
         */
        public function __construct(
            Context $context,
            PageFactory $resultPageFactory
        ) {
            parent::__construct($context);
            $this->resultPageFactory = $resultPageFactory;
            $this->context = $context;
        }
    
        /**
         * Load the page defined in view/frontend/layout/samplenewpage_index_index.xml
         *
         * @return \Magento\Framework\View\Result\\Magento\Framework\View\Result\Page
         */
        public function execute()
        {
            return $this->resultPageFactory->create();
        }
    }


##Magento 2 Block

Shortcode: `mblock`

    <?php
    
    namespace $NAMESPACE$\Block;
    
    use Magento\Framework\View\Element\Template;
    use Magento\Framework\View\Element\Template\Context;
    
    class $CLASS$ extends Template
    {
    
        /**
         * Constructor
         *
         * @param Context $context
         * @param array   $data
         */
        public function __construct(
            Context $context,
            array $data = []$DEPENDENCY$
        ) {
            parent::__construct($context, $data);
        }
    }

##Magento 2 Di.xml

Shortcode: `mdi`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
        <preference for="$NAMESPACE$\Api\$CLASSNAME$Interface" type="$NAMESPACE$\Service\$CLASSNAME$" />
    </config>

##Magento 2 Basic layout.xml

Shortcode: `mlayout`

    <?xml version="1.0"?>
    <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" layout="1column" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
        <body>
            <referenceContainer name="content">
                <block class="$NAMESPACE$\$MODULE$\Block\$BLOCK$" name="$NAME$" template="$NAMESPACE$_$MODULE$::$TEMPLATE$.phtml" />
            </referenceContainer>
        </body>
    </page>

##Magento 2 `module.xml`

Shortcode: `mmodule`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
        <module name="$MODULE$" setup_version="1.0.0" />
    </config>

##Magento 2 `routes.xml`

Shortcode `mroutes`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/etc/routes.xsd">
        <router id="$AREA$">
            <route id="$FRONTNAME$" frontName="$FRONTNAME$">
                <module name="$MODULE$" />
            </route>
        </router>
    </config>

##Magento 2 `system.xml`

Shortcode `msystem`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Config:etc/system_file.xsd">
        <system>
            <section id="$MOODULE_NAME$" translate="label" type="text" sortOrder="300" showInDefault="1" showInWebsite="1" showInStore="1">
                <label>$LABEL$</label>
                <tab>$TAB$</tab>
                <resource>$RESOURCE$</resource>
                <group id="$MOODULE_NAME$" translate="label" type="text" sortOrder="300" showInDefault="1" showInWebsite="0" showInStore="0">
                    <label>$LABEL$</label>
                    <field id="$FIELD_ID$" translate="label" type="select" sortOrder="1" showInDefault="1" showInWebsite="1" showInStore="1">
                        <label>$FIELD_LABEL$</label>
                        <source_model>$SOURCE_MODEL$</source_model>
                    </field>
                </group>
            </section>
        </system>
    </config>

##Magento 2 `acl.xml`

Shortcode `macl`

    <?xml version="1.0"?>
    <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Acl/etc/acl.xsd">
        <acl>
            <resources>
                <resource id="Magento_Backend::admin">
                    <resource id="Magento_Backend::content">
                        <resource id="$NAMESPACE$::$ACTION$" title="$TITLE$" sortOrder="10" />
                    </resource>
                </resource>
            </resources>
        </acl>
    </config>

##Magento 2 menu.xml

Shortcode `mmenu`

    <?xml version="1.0"?>
     <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Backend:etc/menu.xsd">
         <menu>
             <add id="$NAMESPACE$::$ACTION$" action="$URL$" title="$TITLE$" module="$NAMESPACE$" sortOrder="100" parent="Magento_Backend::content" resource="$NAMESPACE$::$ACTION$" />
         </menu>
     </config>

##Magento 2 Block Grid Container

Shortcode `mgrid`

    <?php
    
    namespace $COMPANY$\$MODULE$\Block\Adminhtml;
    
    use Magento\Backend\Block\Widget\Grid\Container;
    
    class $CLASS$ extends Container
    {
        protected function _construct()
        {
            $this->_controller = 'adminhtml_$CONTROLLER$';
            $this->_blockGroup = '$COMPANY$_$MODULE$';
            $this->_headerText = __('$TITLE$');
            parent::_construct();
        }
    
    }

##Magento 2 Unit Test

Shortcode `mtest`

    <?php
    
    namespace $NAMESPACE$;
    
    use PHPUnit_Framework_TestCase;
    
    class $CLASS$Test extends PHPUnit_Framework_TestCase
    {
    
    }

##Magento 2 Backend Controller

Shortcode `mbcontroller`

    <?php
     namespace $COMPANY$\$MODULE$\Controller\Adminhtml\$DIR$;
     
     use Magento\Backend\App\Action as BackendAction;
     use Magento\Backend\App\Action\Context;
     use Magento\Framework\View\Result\PageFactory;
     
     class $ACTION_NAME$ extends BackendAction
     {
     
         const ADMIN_RESOURCE = '$COMPANY$_$MODULE$::$ACTION_LOWER$';
     
         const PAGE_TITLE = '$PAGE_TITLE$';
     
         /**
          * @var PageFactory
          */
         protected $resultPageFactory;
     
         /**
          * @param Context $context
          * @param PageFactory $resultPageFactory
          */
         public function __construct(
             Context $context,
             PageFactory $resultPageFactory
         ) {
             parent::__construct($context);
             $this->resultPageFactory = $resultPageFactory;
         }
     
         /**
          * Index action
          *
          * @return \Magento\Framework\View\Result\Page
          */
         public function execute()
         {
             /** @var \Magento\Framework\View\Result\Page $resultPage */
             $resultPage = $this->resultPageFactory->create();
             $resultPage->setActiveMenu(static::ADMIN_RESOURCE);
             $resultPage->addBreadcrumb(__(static::PAGE_TITLE), __(static::PAGE_TITLE));
             $resultPage->getConfig()->getTitle()->prepend(__(static::PAGE_TITLE));
     
             return $resultPage;
         }
     
         /**
          * Is the user allowed to view the blog post grid.
          *
          * @return bool
          */
         protected function _isAllowed()
         {
             return $this->_authorization->isAllowed(static::ADMIN_RESOURCE);
         }
     
     }

##Magento 2 jQuery Plugin Template
 
Shortcode `mjquery`
 

    ;require(['jquery'], function ($) {
    
        /**
         * Declare a namespace if it doesn't already
         * exist.
         */
        if (!$.$COMPANY$) {
            $.$COMPANY$ = {};
        }
    
        /**
         * Colour switching plugin declaration.
         *
         * @param element
         * @param  options
         * @constructor
         */
        $.$COMPANY$.$MODULE$ = function (element, options) {
    
            /**
             * This variable is used because it's
             * easier than binding `this`
             *
             * @type {$.$COMPANY$.$MODULE$}
             */
            var base = this;
    
            /**
             * Accessor to the element we are manipulating.
             *
             * @type {*|jQuery|HTMLElement}
             */
            base.$element = $(element);
            base.element = element;
    
            /**
             * Add a reverse reference to the plugin.
             */
            base.$element.data("$COMPANY$.$MODULE$", base);
    
            /**
             * Plugin constructor
             */
            base.init = function () {
                base.options = $.extend({}, $.$COMPANY$.$MODULE$.defaultOptions, options);
    
            };
    
            /**
             * Initialize the plugin.
             */
            base.init();
        };
    
        /**
         * Default options for the plugin.
         *
         * @type
         */
        $.$COMPANY$.$MODULE$.defaultOptions = {};
    
        /**
         * Setup the plugin, this will override the default
         * options with the object passed in instantiation.
         *
         * @constructor
         *
         * @param options
         */
        $.fn.$COMPANY$_$MODULE$ = function
            (options) {
            return this.each(function () {
                (new $.$COMPANY$.$MODULE$(this, options));
            });
        };
    
    });

##Magento 2 Model

Shortcode `mmodel`

    <?php
    
    namespace $NAMESPACE$\Model;
    
    use Magento\Framework\Model\AbstractModel;
    
    /**
     * Class $CLASS$
     *
     * @package $NAMESPACE$\Model
     */
    class $CLASS$ extends AbstractModel
    {
    
        /**
         * Prefix of model events names
         *
         * @var string
         */
        protected $_eventPrefix = '$EVENT_PREFIX$';
    
        /**
         * Initialize resource model
         *
         * @return void
         */
        protected function _construct()
    {
        $this->_init('$NAMESPACE$\Model\ResourceModel\$CLASS$');
    }
    
    }


##Magento 2 Resource Model

Shortcode `mresourcemodel`

    <?php
    
    namespace $NAMESPACE$\Model\ResourceModel;
    
    use Magento\Framework\Exception\LocalizedException;
    use Magento\Framework\Model\AbstractModel;
    use Magento\Framework\Model\ResourceModel\Db\AbstractDb;
    use Magento\Framework\Model\ResourceModel\Db\Context;
    use Magento\Framework\Stdlib\DateTime\DateTime;
    
    /**
     * Class $CLASS_NAME$
     *
     * @package $NAMESPACE$\Model\ResourceModel
     */
    class $CLASS_NAME$ extends AbstractDb
    {
        /**
         * Initialize resource model
         *
         * @return void
         */
        protected function _construct()
        {
            $this->_init('$TABLE_NAME$', '$POST_ID$');
        }
    
    }

##Magento 2 Resource Collection

Shortcode `mcollection`

    <?php
    
    namespace $NAMESPACE$\Model\ResourceModel\$RESOURCE$;
    
    use Magento\Framework\Model\ResourceModel\Db\Collection\AbstractCollection;
    
    /**
     * Class Collection
     *
     * @package $NAMESPACE$\Model\ResourceModel\$RESOURCE$
     */
    class Collection extends AbstractCollection
    {
        /**
         * @var string
         */
        protected $_idFieldName = '$ID_FIELD_NAME$';
    
        /**
         * Define the resource model & the model.
         *
         * @return $this
         */
        protected function _construct()
        {
            $this->_init('$NAMESPACE$\Model\$RESOURCE$', '$NAMESPACE$\Model\ResourceModel\$RESOURCE$');
    
            return $this;
        }
    
    }

##Magento 2 Database Schema Install

Shortcode `mschema`

    <?php namespace $NAMESPACE$\Setup;
    
    use Magento\Framework\Setup\InstallSchemaInterface;
    use Magento\Framework\Setup\ModuleContextInterface;
    use Magento\Framework\Setup\SchemaSetupInterface;
    use Magento\Framework\DB\Ddl\Table;
    
    class InstallSchema implements InstallSchemaInterface
    {
        /**
         * Installs DB schema for a module
         *
         * @param SchemaSetupInterface $setup
         * @param ModuleContextInterface $context
         * @return $this
         */
        public function install(
        SchemaSetupInterface $setup,
        ModuleContextInterface $context $DEPENDENCY$
        )
        {
            $installer = $setup;
    
            $installer->startSetup();
    
    
            $installer->endSetup();
    
            return $this;
        }
    
    }
